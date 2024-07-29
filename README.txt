# Intel_XL710_unlock
Credit git: https://github.com/bibigon812/xl710-unlocker

Testado em OS Linux base debian.

Realize instalação de arquivos necessário: apt-get install build-essential && apt-get install git
Realize download dos arquivos: git clone https://github.com/wallysonpereira/Intel_XL710_unlock
Navegue até a pasta: cd Intel_XL710_unlock
Utilize o comando Make para compilar o aplicativo: make
Encontre o código da sua placa: dmesg | grep i40
[4.894735] i40e: Intel(R) Ethernet Connection XL710 Network Driver
[4.894741] i40e: Copyright (c) 2013 - 2019 Intel Corporation.
[4.913435] i40e 0000:08:00.0: fw 9.110.72185 api 1.15 nvm 9.10 0x8000d01e 1.3179.0 [8086:1583] [8086:0001]
[5.031918] i40e 0000:08:00.0: MAC address: 9c:69:b4:65:11:xx
[5.032221] i40e 0000:08:00.0: FW LLDP is enabled
[5.044405] i40e 0000:08:00.0: PCI-Express: Speed 8.0GT/s Width x8

Com base no MAC identifique nome da interface: ip addr
3: ens3f0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 9c:69:b4:65:11:xx brd ff:ff:ff:ff:ff:ff
    altname enp8s0f0
5: ens3f1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 9c:69:b4:65:11:x1 brd ff:ff:ff:ff:ff:ff
    altname enp8s0f1

Execute o desbloqueio: ./xl710_unlock -n ens3f0 -i 0x1583
