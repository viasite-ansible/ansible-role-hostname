# -*- mode: ruby -*-
# vi: set ft=ruby :

hostname_avahi = ENV.key?('HOSTNAME_AVAHI') ? ENV['HOSTNAME_AVAHI'] : 'false'
Vagrant.configure('2') do |config|
  config.vm.define 'anxs' do |c|
    c.vm.box = 'ubuntu/trusty64'
    c.vm.network :private_network, ip: '192.168.88.12'
    c.vm.hostname = 'anxs.local'
    c.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'test.yml'
      ansible.sudo = true
      ansible.inventory_path = 'vagrant-inventory'
      ansible.host_key_checking = false
      ansible.extra_vars = {
        hostname_avahi: hostname_avahi
      }
    end
  end
end
