# -*- mode: ruby -*-
# # vi: set ft=ruby :
#
#
file_to_disk1= 'tmp/host1disk2.vdi'
file_to_disk2= 'tmp/host2disk2.vdi'
file_to_disk3= 'tmp/host3disk2.vdi'
file_to_disk4= 'tmp/host4disk2.vdi'

Vagrant.configure("2") do |config|
# Use the same key for each machine
config.ssh.insert_key = false

  config.vm.define "host1" do |host1|
    host1.vm.box = "centos/7"
    host1.vm.hostname = 'host1'
    host1.vm.box_url = "centos/7"

    host1.vm.network :private_network, ip: "192.168.56.101"
    host1.vm.network :forwarded_port, guest: 9093, host: 9093#

    host1.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--name", "host1"]
    end

# create the second disk and attach it
  config.vm.provider "virtualbox" do |vb|
      unless File.exist?(file_to_disk1)
          vb.customize ['createhd', '--filename', file_to_disk1, '--variant', 'Fixed', '--size', 1 * 1024]
      end
      vb.customize ['storageattach', :id,  '--storagectl', 'IDE Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk1]
  end
  end

  config.vm.define "host2" do |host2|
    host2.vm.box = "centos/7"
    host2.vm.hostname = 'host2'
    host2.vm.box_url = "centos/7"

    host2.vm.network :private_network, ip: "192.168.56.102"

    host2.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--name", "host2"]
    end
# create the second disk and attach it
  config.vm.provider "virtualbox" do |vb|
      unless File.exist?(file_to_disk2)
          vb.customize ['createhd', '--filename', file_to_disk2' , '--variant', 'Fixed', '--size', 1 * 1024]
      end
      vb.customize ['storageattach', :id,  '--storagectl', 'IDE Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk2]
  end
  end

 config.vm.define "host3" do |host3|
    host3.vm.box = "centos/7"
    host3.vm.hostname = 'host3'
    host3.vm.box_url = "centos/7"

    host3.vm.network :private_network, ip: "192.168.56.103"
    host3.vm.network :forwarded_port, guest: 15672, host: 15672#

    host3.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--name", "host3"]
    end
# create the second disk and attach it
  config.vm.provider "virtualbox" do |vb|
      unless File.exist?(file_to_disk3)
          vb.customize ['createhd', '--filename',  file_to_disk3, '--variant', 'Fixed', '--size', 1 * 1024]
      end
      vb.customize ['storageattach', :id,  '--storagectl', 'IDE Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk3
  end
  end

  config.vm.define "host4" do |host4|
    host4.vm.box = "centos/7"
    host4.vm.hostname = 'host4'
    host4.vm.box_url = "centos/7"

    host4.vm.network :private_network, ip: "192.168.56.104"
    host4.vm.network :forwarded_port, guest: 15672, host: 25672#

    host4.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--name", "host4"]
    end
# create the second disk and attach it
  config.vm.provider "virtualbox" do |vb|
      unless File.exist?(file_to_disk4)
          vb.customize ['createhd', '--filename', file_to_disk4, '--variant', 'Fixed', '--size', 1 * 1024]
      end
      vb.customize ['storageattach', :id,  '--storagectl', 'IDE Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk4]
  end
  end


end
