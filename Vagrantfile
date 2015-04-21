# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Basic default configuration
  config.vm.box = "http://aka.ms/vagrant-${os.version.prefix}${target-os.version}-${vagrant-basebox.browser.suffix}"

  # Basic network configuration
  config.vm.host_name = "${vagrant-box.name}"

  # Tell them we are using Windows without SSH
  config.vm.communicator = "winrm"

  # Share the build folder as read only
  config.vm.synced_folder "${build.dir}", "${vagrant-build.dir}"
  config.vm.synced_folder "${reports.dir}", "${vagrant-reports.dir}"
  config.vm.synced_folder "${src.dir}", "${vagrant-src.dir}"
  config.vm.synced_folder "${lib.dir}", "${vagrant-lib.dir}"

  # Extend the timeout for initial connection
  config.vm.boot_timeout = 600

  config.vm.provider "virtualbox" do |vb|
    host = RbConfig::CONFIG['host_os']

    # Give VM 3Gb system memory & access to 2 cpu cores on the host
    mem = 3072
    cpus = 2

    vb.customize ["modifyvm", :id, "--memory", mem]
    vb.customize ["modifyvm", :id, "--cpus", cpus]
  end

  config.vm.define :"${vagrant-box.name}" do |t|
    end
end
