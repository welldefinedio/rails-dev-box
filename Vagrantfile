# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Ubuntu Server 14.04 LTS (Trusty Tahr)
  config.vm.box = "ubuntu/trusty64"

  # need a private network for NFS shares to work
  config.vm.network "private_network", type: "dhcp"

  # Mount NFS shared folder
  config.vm.synced_folder ".", "/app", type: "nfs"

  # Rails Server Port Forwarding
  config.vm.network "forwarded_port", guest: 3000, host: 3000

  # SSH forwarding, see https://coderwall.com/p/p3bj2a/
  config.ssh.forward_agent = true

  # Change some default options for better experience, up memory and change VM name
  config.vm.provider :virtualbox do |vb|
    vb.memory = 4096
  end

  config.vm.provision :shell, path: "script/vagrant-bootstrap", keep_color: true
end
