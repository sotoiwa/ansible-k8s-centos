# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  (1..3).each do |i|

    if i == 1 then
      vm_name = "master"
    else
      vm_name = "node#{i-1}"
    end
      
    config.vm.define vm_name do |s|

      # ホスト名
      s.vm.hostname = vm_name
      # ノードのベースOSを指定
      s.vm.box = "centos/7"
      # ネットワークを指定
      # pod-network-cidrと重ならないように注意
      # private_ip = "192.168.33.#{i+10}"
      private_ip = "172.16.33.#{i+10}"
      s.vm.network "private_network", ip: private_ip

      # ノードのスペックを指定
      s.vm.provider "virtualbox" do |v|
        v.gui = false        
        if i == 1 then
          v.cpus = 2
          v.memory = 1024
        else
          v.cpus = 1
          v.memory = 1024
        end
      end
    
    end
  end
end