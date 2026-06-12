---
title: "backtrack5-usb wificard"
date: 2012-12-29
forum: Any Other OS
---

### Post by Th3J0k3r on 2012-12-29
installed backtrack5 in vbox and bought a netgear n150 wireless usb adapter to use with it. so far ive got it to show with lsusb command, but actually using it is a no go. ive even tried configuring it in the /etc/network/interfaces file and yet iwconfig doesn't see wlan0. im relevantly new to linux, as in ive had 2 linux classes through school mostly covering red hat/fedora and focused more on the gui so some in depth detail would be appreciated.

---

### Post by uRock on 2012-12-29
ubuntu can be different when getting drivers to work.

Moved to Other OS/Distro Talk.

---

### Post by Th3J0k3r on 2012-12-29
true, just saying i do have a little experience in the linux field. still i have no clue what to do to actually fix my problem

---

### Post by BertN45 on 2012-12-29
[COLOR="Blue"]**TRY THIS **[/COLOR]:
Use Ubuntu Software Center or Synaptic Package Manager to install [COLOR="Blue"]linux-firmware-nonfree[/COLOR] or run [COLOR="blue"]sudo apt-get install linux-firmware-nonfree[/COLOR] in a terminal.

See [http://ubuntuforums.org/showthread.php?t=1594592&page=2](http://ubuntuforums.org/showthread.php?t=1594592&page=2) and especially entry 13.

---

### Post by Th3J0k3r on 2012-12-29
> **BertN45 said:**
> If you type in the terminal [COLOR=Blue]lsusb[/COLOR]
results:
Bus 001 Device 004: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 002: ID 80ee:0021  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

> If you type [COLOR=blue]ifconfig[/COLOR].
results:
eth0      Link encap:Ethernet  HWaddr 08:00:27:8b:54:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 08:00:27:4e:65:86  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe4e:6586/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9578 (9.5 KB)  TX bytes:27828 (27.8 KB)

eth2      Link encap:Ethernet  HWaddr 08:00:27:a9:8b:8f  
          inet6 addr: fe80::a00:27ff:fea9:8b8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21855 (21.8 KB)  TX bytes:21855 (21.8 KB)

---

### Post by Th3J0k3r on 2012-12-30
> **BertN45 said:**
> [COLOR=Blue]**TRY THIS **[/COLOR]:
Use Ubuntu Software Center or Synaptic Package Manager to install [COLOR=Blue]linux-firmware-nonfree[/COLOR] or run [COLOR=blue]sudo apt-get install linux-firmware-nonfree[/COLOR] in a terminal.

See [http://ubuntuforums.org/showthread.php?t=1594592&page=2](http://ubuntuforums.org/showthread.php?t=1594592&page=2) and especially entry 13.

ran it from terminal, still no functionality from my usb adapter. and wlan still doesn't show in ifconfig.

edit: ran it a second time incase of error and got

  Error! Bad return status for module build on kernel: 2.6.38 (i686)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.1.6/build/ for more information.
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up linux-firmware-nonfree (1.8) ...
Errors were encountered while processing:
 virtualbox-ose-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

make.log returns the following when opened in gedit:

DKMS make.log for virtualbox-ose-3.1.6 for kernel 2.6.38 (i686)
Sun Dec 30 04:02:27 EST 2012
make: Entering directory `/usr/src/linux-source-2.6.38'
  LD      /var/lib/dkms/virtualbox-ose/3.1.6/build/built-in.o
  LD      /var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/built-in.o
  CC [M]  /var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.o
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c: In function &#8216;VBoxDrvLinuxInit&#8217;:
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c:443: error: &#8216;nmi_watchdog&#8217; undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c:443: error: (Each undeclared identifier is reported only once
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c:443: error: for each function it appears in.)
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c:443: error: &#8216;NMI_IO_APIC&#8217; undeclared (first use in this function)
/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.c:457: error: &#8216;nmi_active&#8217; undeclared (first use in this function)
make[2]: *** [/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv/linux/SUPDrv-linux.o] Error 1
make[1]: *** [/var/lib/dkms/virtualbox-ose/3.1.6/build/vboxdrv] Error 2
make: *** [_module_/var/lib/dkms/virtualbox-ose/3.1.6/build] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.38'

---

### Post by BertN45 on 2012-12-30
It seems you use a very old Virtualbox version the OSE version 3.1.6, the current Virtualbox version from Oracle is 4.2.4 and there is no real difference between OSE and other versions anymore.
Why not download it from the virtualbox.org website and install the newest Virtualbox?

---

### Post by Th3J0k3r on 2012-12-30
in doing that will i have lost all of my work that ive done within my vm's?

---

### Post by haqking on 2012-12-30
People seem to forget that Backtrack is not meant for daily OS use on a desktop, it is built for purpose OS for security auditing and penetration testing.

Just because it is based on Ubuntu does not mean everything is the same.  The kernel is specific for the wireless cards it supports based on injection etc.

[http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

Get one that is supported out of the box for the tools you wish to use or compile your own drivers for the tools you want to use.

Backtrack assumes more than any other Linux that you know what you are doing.

If it is the wna1100 then see here [http://ubuntuforums.org/showpost.php?p=10539611&postcount=4](http://ubuntuforums.org/showpost.php?p=10539611&postcount=4)

which i suspect is the tool you want it to work with in BT.

---

### Post by Th3J0k3r on 2012-12-30
> **haqking said:**
> People seem to forget that Backtrack is not meant for daily OS use on a desktop, it is built for purpose OS for security auditing and penetration testing.

Just because it is based on Ubuntu does not mean everything is the same.  The kernel is specific for the wireless cards it supports based on injection etc.

If it is the wna100 then see here [http://ubuntuforums.org/showpost.php?p=10539611&postcount=4](http://ubuntuforums.org/showpost.php?p=10539611&postcount=4)

which i suspect is the tool you want it to work with in BT.


first off, in order to use backtrack the way it's meant to be used i need to get the wireless working as to being able to surf the web, then move on to configuring say gerix to use it. second i took injection and packet capture into thought when i bought the usb adapter, actually did weeks of research and couldn't find an out of the box solution for backtrack that was in a local store, as i do not have a credit card, nor would i feel comfy using one online anyway. and lastly the netgearr n150 is a wna 1100 not 100, tho i assume you meant 1000. but thank you for trying to clear some of that up. also i am consulting on the problem on a backtrack specific forum as well, tho people there seem not to be particularly helpful unlike the people here who are at least trying.

edit: i have, since writing the above, opened the link you posted and started to follow along.guess i shouldnt assume something from a missing character.

edit #2: after looking at the link provided you're on the right track, however it seems to me that their patching monitor modes and packet injections... as of right now i cant even use the card to pick up internet, it's effectively a paperweight.

---

### Post by haqking on 2012-12-30
> **Th3J0k3r said:**
> first off, in order to use backtrack the way it's meant to be used i need to get the wireless working as to being able to surf the web, then move on to configuring say gerix to use it. second i took injection and packet capture into thought when i bought the usb adapter, actually did weeks of research and couldn't find an out of the box solution for backtrack that was in a local store, as i do not have a credit card, nor would i feel comfy using one online anyway. and lastly the netgearr n150 is a wna 1100 not 100, tho i assume you meant 1000. but thank you for trying to clear some of that up. also i am consulting on the problem on a backtrack specific forum as well, tho people there seem not to be particularly helpful unlike the people here who are at least trying.

edit: i have, since writing the above, opened the link you posted and started to follow along.guess i shouldnt assume something from a missing character.

I wasnt saying it was a 100/1100 I was assuming as you hadnt told us.

And just so you know, once you get it working if you do, the tools such nas Gerix and others wont be supported here.

Good luck with the card.

and following post number 4 wasnt your best solution as it is not UBUNTU but backtrack ;-)

The post i linked to does work for aircrack however so should be good.

I also take it you ae running an old version of BT as you are on an old kernel which was BT 5 the first, it is now in RC3 using kernel 3.2x
Peace

---

### Post by dodo3773 on 2012-12-30
> **haqking said:**
> 
I also take it you ae running an old version of BT as you are on an old kernel which was BT 5 the first, it is now in RC3 using kernel 3.2x
Peace

This ^^. Update your kernel. The kernel includes the driver unless it needs firmware (even in this case the kernel will load that firmware). Don't think about it in terms of distro X vs distro Y. Think about it in terms of driver / kernel / firmware. Try just updating your system maybe. Also, run "ifconfig -a" to see if the device is there but isn't / cannot be brought up instead of just "ifconfig".

---

### Post by Th3J0k3r on 2012-12-30
> **haqking said:**
> I wasnt saying it was a 100/1100 I was assuming as you hadnt told us.

And just so you know, once you get it working if you do, the tools such nas Gerix and others wont be supported here.

Good luck with the card.

and following post number 4 wasnt your best solution as it is not UBUNTU but backtrack ;-)

The post i linked to does work for aircrack however so should be good.

I also take it you ae running an old version of BT as you are on an old kernel which was BT 5 the first, it is now in RC3 using kernel 3.2x
Peace

was just a clarification on my part, as your op did say 100 i was assuming you meant 100 or 1000. i understand the specific programs inside backtrack are another problem to be solved later, hence my second edit (before reading this post but after reading the link on your last) about also being on a backtrack specific forum. and yes i am running backtracks first release of 5

>  This ^^. Update your kernel. The kernel includes the driver unless it  needs firmware (even in this case the kernel will load that firmware).  Don't think about it in terms of distro X vs distro Y. Think about it in  terms of driver / kernel / firmware. Try just updating your system  maybe. Also, run "ifconfig -a" to see if the device is there but isn't /  cannot be brought up instead of just "ifconfig". 

ifconfig -a did not return anything regarding my device or wlan0. i am currently dling the latest backtrack...

---

### Post by haqking on 2012-12-30
> **Th3J0k3r said:**
>  i am currently dling the latest backtrack...

You should have better luck as it is kernel 3.2.6

The one you were using was 2.6.38

Though i cannot comment on your card in my experience.  I tend to use ALFA devices all the time in BT these days, it has been a while since i have used anything else.

---

