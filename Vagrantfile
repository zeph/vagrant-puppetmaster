# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.define :master do |master_config|

      # All Vagrant configuration is done here. The most common configuration
      # options are documented and commented below. For a complete reference,
      # please see the online documentation at vagrantup.com.
      master_config.vm.host_name = "puppet.grahamgilbert.dev"
      # Every Vagrant virtual environment requires a box to build off of.
      master_config.vm.box = "ubuntu"
    
      # The url from where the 'master_config.vm.box' box will be fetched if it
      # doesn't already exist on the user's system.
      master_config.vm.box_url = "http://files.vagrantup.com/precise64.box"
      
      # If you're using VMWare Fusion rather than Virtualbox, you'll want to use this box_url instead
      # master_config.vm.box_url = "http://files.vagrantup.com/precise64_vmware_fusion.box"
    
      # Assign this VM to a host-only network IP, allowing you to access it
      # via the IP. Host-only networks can talk to the host machine as well as
      # any other machines on the same network, but cannot be accessed (through this
      # network interface) by any external networks.
      master_config.vm.network :hostonly, "192.168.33.10"
        
      # Share an additional folder to the guest VM. The first argument is
      # an identifier, the second is the path on the guest to mount the
      # folder, and the third is the path on the host to the actual folder.
      
      master_config.vm.provision :shell, :path => "puppet_master.sh"
      # Enable the Puppet provisioner
      master_config.vm.provision :puppet, :module_path => "VagrantConf/modules", :manifests_path => "VagrantConf/manifests", :manifest_file  => "default.pp"

      master_config.vm.share_folder "manifests", "/etc/puppet/manifests", "puppet/manifests"
      master_config.vm.share_folder "modules", "/etc/puppet/modules", "puppet/modules"
      master_config.vm.share_folder "hieradata", "/etc/puppet/hieradata", "puppet/hieradata"
  end
end
