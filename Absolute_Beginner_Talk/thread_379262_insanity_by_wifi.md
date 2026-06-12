---
title: "insanity by wifi"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by kyl87 on 2007-03-08
Hi, I'm completely new to linux.  I installed edgy (dual boot /w xp sp2) and I'm trying to get my wifi working using a broadcom card.  I've looked everywhere and tried everything with little success.  I finally thought I had something when I tried the ndiswrapper instructions @ [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).  I went through the tutorial and everything went normally, there were no errors of any kind.  There is still no wifi, however, which confuses me because:

```

kylebabich@pheonix:~$ ndiswrapper -l
Installed drivers:
bcmwl5          driver installed, hardware present 

kylebabich@pheonix:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

```

If the driver is installed and working then what's going on here:

```

kylebabich@pheonix:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

kylebabich@pheonix:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:B8:DE:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

```

I also know Ubuntu sees my card because:

```

lspci
...
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

lspci -n
....
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

And when I try to access the network manually:

```

kylebabich@pheonix:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

I have no idea what I should do next.  I feel like I'm close to getting my wifi working, but I'm lost on what to do next.  Where did I go wrong/what am I missing?

---

### Post by Bachstelze on 2007-03-08
```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

### Post by kyl87 on 2007-03-08
> **HymnToLife said:**
> ```
sudo depmod -a
sudo modprobe ndiswrapper
```

Just tried it.  No error, no noticeable result.  After running those commands iwconfig, ifconfig, and ifup wlan0 still produce the exact same results.

---

### Post by Bachstelze on 2007-03-08
Did you blacklist the bcm43xx driver as the Wiki says ?

---

### Post by kyl87 on 2007-03-08
Yep it's blacklisted in /etc/modprobe.d/blacklist.  I rebooted after it was blacklisted like the wiki says too.  I even tried entering the command again after it was rebooted:

```

kylebabich@pheonix:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
kylebabich@pheonix:~$ sudo depmod -a
kylebabich@pheonix:~$ sudo modprobe ndiswrapper
kylebabich@pheonix:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:B8:DE:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1284 (1.2 KiB)  TX bytes:1284 (1.2 KiB)

kylebabich@pheonix:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

kylebabich@pheonix:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

---

### Post by kyl87 on 2007-03-08
I guess I might be out of luck with the card for now.  I found this...

> 
Sadly, the wireless board (Broadcom BCM1390M, or 4311) cannot be driven by current bcm43xx kernel driver. There is ndiswrapper, but the HP supplied Windows XP driver cannot be loaded properly since it complains it's 64-bit, so I had to use Acer-supplied 32-bit driver. That doesn't work very well, since irq conflicts with nvidia driver and usually hangs as soon as the wireless traffic goes up.


...[here](http://www.linuxquestions.org/questions/showthread.php?p=2433046#post2433046).

---

### Post by nevermind_quack on 2007-03-16
Ndiswrapper doesn't work with the bcm4310 driver if you have the proprietary nvidia driver running edgy or earlier.  After a few minutes of it working it blows up...

After reading the bug reports it looks like this requires a newer version of the kernel. I dist-upgraded to feisty, a 2.6.20 kernel, and ndiswrapper works beautifully. The bcm43xx driver still isn't working well for me, it doesn't list my AP and is generally picky and buggy. Note that feisty isn't stable yet, so it may not be worth it to upgrade.  If you want this is what to do:

1. change all references to edgy in your /etc/apt/sources.list to fiesty
2. apt-get update
3. apt-get dist-upgrade
4. wait for the download and work through upgrading EVERYTHING (this will take some time)
5. sort out the bugs and brokens from the upgrade (e.g. I had to tweak my xorg.conf and remove all my .folders, bleh, ugh...)
6. ndiswrapper install as described
7. add bcm43xx to the blacklist as mentioned, make sure bcm43xx is not in /etc/modules and ndiswrapper is, lsmod and look for bcm43xx to verify
8. iwlist scan to see what you can see and enjoy

---

### Post by nevermind_quack on 2007-03-16
Kyl87, After reading this thread a little more carefully, I'm not sure you'll need to follow my directions above.  Your problem may be more basic. Try this and post back the output.

This driver worked for me [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) so you may want to try it. Some stuff to try below, # starts a comment ;)

# reinstall ndiswrapper driver
sudo apt-get install cabextract
wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe
# now the exe is unzipped so to speak in your current folder
sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l


# see if you're running the nvidia driver
cat /etc/X11/xorg.conf | grep nvidia

# see what's actually going on with your driver
lsmod | grep bcm43xx
lsmod | grep ndiswrapper

# remove both drivers for your card (won't hurt if they aren't there either)
# load the ndiswrapper driver
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

#now your ifconfig and iwconfig should see an eth1
iwlist scan

If you see your network of choice you're there.  Just follow somebody's instructions from that point about your connect method of choice.  For me, networkmanager works really well since i'm not always associating to the same AP.  'apt-get install network-manager network-manager-gnome' for that, then run nm-applet for the gnome applet.  Don't install it until after you verify your driver works though as it takes over some basic functions of networking.

I should be asleep so this may not make sense, but... Good luck!

---

