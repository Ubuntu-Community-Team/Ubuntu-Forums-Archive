---
title: "broadcom bcm4306"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mrsempai on 2007-06-04
im having some problems with my wireless... its a broadcom bcm4306...

searching in google i found this...  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28%28WifiDocs%7CDriver%7Cbcm43xx%7CFeisty%29%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28%28WifiDocs%7CDriver%7Cbcm43xx%7CFeisty%29%29)

im using ubuntu 7.04 and i know there is a guide to do it there, but i dont understand it... can someone help me?

thx

---

### Post by Cedfelix on 2007-06-04
I just set up a very similar card on my laptop. Follow the link in my signature.

---

### Post by gunbladeiv on 2007-06-04
> **mrsempai said:**
> im having some problems with my wireless... its a broadcom bcm4306...

searching in google i found this...  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28%28WifiDocs%7CDriver%7Cbcm43xx%7CFeisty%29%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx?highlight=%28%28WifiDocs%7CDriver%7Cbcm43xx%7CFeisty%29%29)

im using ubuntu 7.04 and i know there is a guide to do it there, but i dont understand it... can someone help me?

thx

choose which method would you like to use?
ndiswrapper of fwcutter?

im using dapper(6.06 version of ubuntu) and ndiswrapper works for me.  And i had no prblm with the speed rate until now.  
I've tried ndiswrapper with 7.04(Feisty) but it wont work.  fwcutter works with my broadcom on feisty but im having trouble with the unstalble driver from the firmware.  You have to decide which method you want to use.

---

### Post by mrsempai on 2007-06-05
ok, i followed the link in your signature and downloaded the native bcm43xx driver since my card is diferent than yours... but when i try to install it (by double clicking it like it says) and an error pops up... heres a screen shot

[[IMG]http://img507.imageshack.us/img507/5024/screenshotgq8.th.png[/IMG]](http://img507.imageshack.us/my.php?image=screenshotgq8.png)

---

### Post by Cedfelix on 2007-06-05
Sorry, I cant see the screenshot, the resolution is too low. I can't read the text.

---

### Post by mrsempai on 2007-06-05
click on it, it will take you to a big one

---

### Post by mrsempai on 2007-06-05
bump... 

can someone check the screen shot and help me out plz?? thx ^^

---

### Post by Cedfelix on 2007-06-05
I'm not sure what happened there, did you try the command line in terminal? Navigate to you desktop using "cd" then type```
 sudo dpkg bcm43xx_compwiz18.1-all.deb
```

---

### Post by mrsempai on 2007-06-05
i followed this guide

[http://ubuntuforums.org/showthread.php?t=201902&page=1](http://ubuntuforums.org/showthread.php?t=201902&page=1)

was having problems with the wireless card not showing so i used  this guide

[http://ubuntuforums.org/showthread.php?t=340689&page=5](http://ubuntuforums.org/showthread.php?t=340689&page=5)

and changed ndiswapper version for 1.44 where needed... now i can se my wireless card again, but cant rename it from eth0 to wlan0

here's some information... can someone help? i know im almost done!

```
mrsempai@lp2p:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:90:4b:cb:84:2a arp 1
#eth1 mac 00:03:25:20:3a:d0 arp 1


```


```
mrsempai@lp2p:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


#iface eth1 inet dhcp

#auto eth1

#iface eth1 inet dhcp

#auto eth1

```

```
mrsempai@lp2p:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

