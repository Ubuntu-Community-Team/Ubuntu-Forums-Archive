---
title: "[SOLVED] Totally New to  Ubuntu"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Tews on 2008-03-01
Im having problems finding a step by step guide how to install a driver.  In this case its my wireless adapter.  I have the linux driver iwlwifi4965 ucode file but have no earthly idea how to install it.  HELP!

---

### Post by reyhan on 2008-03-01
maybe you must install 

```
wireless assistant,kwifi manager,Rutilt WLAN manager and Kwlan
```

on add / remove application

i hope that's work

---

### Post by trigun on 2008-03-01
if it's source code :

1º extract files
2º enter the directory and ./configure
3º make 
4º sudo make install
5º then you have to enable the driver to start at the boot time

---

### Post by jan quark on 2008-03-01
wowow

perhaps let's have a look if your drivers are already enabled please run this commands in the terminal and post the output please

thank you

```
sudo lshw -C network
```

```
iwconfig
```

---

### Post by bren on 2008-03-01
and if its a driver.bin file then you just need to go to the directory where it is and go


sudo sh driver.bin

or 

sudo ./driver.bin

bren

---

### Post by Tews on 2008-03-01
my problem is that I dont know how to install **anything**!  I have searched the forums and googled till my fingertips are now squares but haven't had any success. Once I get this working Ill be ok, but till then Im in limbo....

---

### Post by zetjee on 2008-03-01
The app which you can use to install software can be found here: applications > add/remove software.

There you have a lot off software, just check the boxes to install! :) 

If you need an app which is not there google for a .deb file. THis can be compared to the .exe op windows.

THis is helpfull?

---

### Post by timbounceback on 2008-03-01
There are many different methods for installing stuff on Linux? What file extension is the driver you're downloading. That can often help. Oh, but follow jan quark's advice first.

---

### Post by Tews on 2008-03-01
> **jan quark said:**
> wowow

perhaps let's have a look if your drivers are already enabled please run this commands in the terminal and post the output please

thank you

```
sudo lshw -C network
```

```
iwconfig
```

Here is the result ...

tom@tom-laptop:~$ sudo lshw -C network 
[sudo] password for tom: 
  *-network               
       description: Ethernet interface 
       product: 88E8055 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:1a:80:1a:31:c2 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       logical name: wmaster0 
       version: 61 
       serial: 00:13:e8:9f:42:ab 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g 
tom@tom-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

tom@tom-laptop:~$

---

### Post by Omnios on 2008-03-01
There is an install link in my signature

---

### Post by jan quark on 2008-03-01
well I guess your wlan card has the right drivers already enabled
> 
configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g 

you have to configure your internet connection
see here:
[https://help.ubuntu.com/7.10/internet/C/index.html](https://help.ubuntu.com/7.10/internet/C/index.html)
ask for more help

for installing stuff 

see here
[LIST]
[*][http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[*][http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[/LIST]

---

### Post by Tews on 2008-03-01
I have it running O:)  Thanks to everyone for their help !!!  Its communities like this one that make the switch from windows to linux so easy!!

---

