---
title: "No Wireless on my Macbook"
date: 2008-01-05
forum: Apple Intel Users
---

### Post by Aifel on 2008-01-05
So, I installed ubuntu, and my wireless doesn't work. In fact, it's not even detected. I have the standard Atheros chipset that came with the 2006 Macbooks. Any and all help would be appreciated. And yes, I've installed NDISwrapper, but it didn't help...

---

### Post by Stu09 on 2008-01-06
I had trouble with NDISwrapper. I followed the Madwifi instructions on the wiki and haven't looked back.

---

### Post by cyberdork33 on 2008-01-07
ndiswrapper requires you to install the windows driver for the card to work.


You should try the latest version of madwifi.

---

### Post by mabovo on 2008-01-07
> **Aifel said:**
> So, I installed ubuntu, and my wireless doesn't work. In fact, it's not even detected. I have the standard Atheros chipset that came with the 2006 Macbooks. Any and all help would be appreciated. And yes, I've installed NDISwrapper, but it didn't help...

Which distro of Ubuntu ?

---

### Post by Aifel on 2008-01-08
> **mabovo said:**
> Which distro of Ubuntu ?
Ubuntu 7.10. And I've tried the HOWTO in the Apple Intel section for MadWif drivers, and they did nothing.

---

### Post by cyberdork33 on 2008-01-08
ok, well, more information would be helpfu. Give the output of the following:
```
ifconfig
```
```
lsmod |grep ath
```
```
lsmod |grep ndiswrapper
```

---

### Post by mabovo on 2008-01-18
```

mabovo@macbook:~/mac_drivers/isight$ iwconfig ath0
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:29  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mabovo@macbook:~/mac_drivers/isight$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:15:E9:79:52:9E
                    ESSID:"bovo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-31 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

mabovo@macbook:~/mac_drivers/isight$ ifconfig
ath0      Link encap:Ethernet  Endereço de HW 00:1b:63:05:81:11  
          endereço inet6: fe80::21b:63ff:fe05:8111/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  Endereço de HW 00:1b:63:05:81:11  
          inet end.: 169.254.3.74  Bcast:169.254.255.255  Masc:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1

eth0      Link encap:Ethernet  Endereço de HW 00:17:f2:df:89:b5  
          inet end.: 192.168.0.100  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::217:f2ff:fedf:89b5/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:12586 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:7825 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:11874800 (11.3 MB) TX bytes:944204 (922.0 KB)
          IRQ:16 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:1461 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:1461 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:74574 (72.8 KB) TX bytes:74574 (72.8 KB)

wifi0     Link encap:Não Especificado  Endereço de HW 00-1B-63-05-81-11-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:4222 erros:0 descartados:0 excesso:0 quadro:211
          Pacotes TX:7929 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:199 
          RX bytes:534894 (522.3 KB) TX bytes:350466 (342.2 KB)
          IRQ:17 

mabovo@macbook:~/mac_drivers/isight$ lsmod |grep ath
ath_rate_sample        16384  1 
ath_pci               167096  0 
wlan                  259232  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               261376  3 ath_rate_sample,ath_pci

mabovo@macbook:~/mac_drivers/isight$ lsmod |grep ndiswrapper
ndiswrapper           243776  0 
usbcore               169392  10 uvcvideo,hci_usb,prism2_usb,ndiswrapper,appleir,usbhid,appletouch,ehci_hcd,uhci_hcd
mabovo@macbook:~/mac_drivers/isight$ 


```

---

### Post by cyberdork33 on 2008-01-20
Do you still need help with this? It looks like your card is working fine.

---

