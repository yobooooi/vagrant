# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.define "dev_env" do |dev_env|
    dev_env.vm.box = "ubuntu/bionic64"

    dev_env.vm.network  "private_network", ip: "192.168.50.9"
    dev_env.vm.network  "public_network"

    # Config to mount/share a folder from the host
    # cpt_dev_env.vm.synced_folder "/foo/bar", "/data/"
    dev_env.vm.provider :virtualbox do |vb|
      vb.cpus = 4
      vb.memory = 4096
      end

    config.vm.provision "shell", path: "scripts/bootscript.sh"
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/setup.yaml"
      end
    end
end
