Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"

  config.vm.provider "virtualbox" do |v|
    v.memory = 8192
    v.cpus = 4
    v.name = "eggcloud"
  end

  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.network "forwarded_port", guest: 5001, host: 5001
  config.vm.network "forwarded_port", guest: 5900, host: 5900
  config.vm.network "forwarded_port", guest: 8443, host: 8443

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.extra_vars = {
      service_name: "localhost"
    }
  end
end
