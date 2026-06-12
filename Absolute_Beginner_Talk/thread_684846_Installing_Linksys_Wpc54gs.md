---
title: "Installing Linksys Wpc54gs"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by R.Schwendler on 2008-02-01
Installing linksys WPC54GS wireless G  pcmcia adapter
on  Gusty 7.1   linux 2.6.22.14
I am new so followed instructions on ndswrapper  web site

1  installed ndiswraper
2 sudo ndiswraper -i lstinds.inf
3 sudo ndiswraper -l              lstinds driver installed
4 ndiswraper -m                    module configured
5 depmod  -a                        no error
6 lspci                                   broadcom  BCM4318
6 lspci -m                             06:00.0 0280 14e4:4318 rev 2
7 iwconfig                           lo nowireless
                                            eth1   iee802.11g   access point invalid
8 dmesg                              bcm43xx error   not available
                                           usbcore reg new interface driver ndiswrapper

9 list syslog               error loading   /lib/firmware/bcm43xx_microcode.fw
                                 ndiswrapper v1.45 loaded (smp=yes)

I did a search on 'bcm43xx'    
found              /lib/modules/2.6.22.14-generic/kernel/ubuntu/wireless/bcm43xx                    
                      /lib/modules/2.6.22.14-generic/kernel/drivers/wireless/bcm43xx

What next??
Rich

---

### Post by wesleybailey on 2008-02-02
You need to blacklist the pre-installed driver **(bcm43xx)** before you can use ndiswrapper.

**1.** Open the blacklist file with this command:

```
sudo gedit /etc/modprobe.d/blacklist
```

**2.** In the new window, on a new line and type: blacklist bcm43xx

**3.** Reboot

You should be able to use the rest of those commands and get it working.

---

### Post by Lokithor on 2008-02-04
> **wesleybailey said:**
> You need to blacklist the pre-installed driver **(bcm43xx)** before you can use ndiswrapper.
**1.** Open the blacklist file with this command:
```
sudo gedit /etc/modprobe.d/blacklist
```
**2.** In the new window, on a new line and type: blacklist bcm43xx
**3.** Reboot
You should be able to use the rest of those commands and get it working.

**Then should the steps be:**
1. sudo gedit /etc/modprobe.d/blacklist
2. In the new window, on a new line, type: blacklist BCM43xx
3. Reboot
4. sudo ndiswrapper -i
5. sudo newswrapper -l
6. sudo ndiswrapper -m
7. depmod -a
8. lspci broadcom bcm4318
9. lspci -m
10. iwconfig (check results)
Is this correct?

Where does the bcm4318 file come from if has been blacklisted?

---

### Post by wesleybailey on 2008-02-04
The bcm48xx driver comes from the windows drivers. 

4. ndiswrapper -i filename.INF

---

### Post by R.Schwendler on 2008-02-04
Ok 
I entered 'blacklist bcm43xx' on a new line  in file /ete/modprobe.d/blacklist
 I removed 'lstinds.inf   using ndiswrapper  -r       this file was for win xp
the plugged in the card  and lspci -n            ==>   14e4:4318
sudo ndiswrapper -i lsbcmnds.inf                  the win9x  vers
ndiswrapper -l       ==>    driver installed device  (14e4:4318) present   Alrernate driver  bcm43xx
Rats
rmmod      bcm43xx               ==>   bcm43xx does not exit in proc/modules 
modprobe -r bcm43xx           ==>  no comment 
sudo modprobe ndiswrapper
dmesg | grep ndiswrapper        ==>    ndiswrapper loaded driver lsbcmnds loaded    wlan0 > eth1
iwconfig     ==>            eth1  essid 'schwendler'  access point 00:12:43:1A:83 !8 

looks ok  ??

I went to the network icon   ===>   no network devices found

went to properties                I am not using   password for wpa or network password
I tried  roaming that did not work  either  

What next

Rich

---

### Post by R.Schwendler on 2008-02-04
I brought up the network manager  propertys      and selected   wep  ascii    and it works

the syslog says it did not like  WPA ' '   so I changed it to wep

Thanks

---

### Post by wesleybailey on 2008-02-05
Awesome, I'm glad to hear you got wireless working.

---

