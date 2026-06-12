---
title: "Powerbook G4 BCM4318 Wireless help (Desperate)"
date: 2007-01-19
forum: Apple PPC Users
---

### Post by Win2Mac2Linux on 2007-01-19
I have run into a desperate dead end with this whole wireless thing.  I tried in the networking section, but I'm thinking I might be better here because of I have a Powerbook.  I have tried several times to resolve this (with help, I'm completely new with this), but to no avail.  My latest steps were this.  I did a fresh install of Ubuntu 6.10 and applied all the updates.  I then followed a how-to from the networking section for my wireless card (BCM4318).  After that, I noticed that the "wireless" option under System>Administration>Networking was missing and only the "wired" and "modem" options were still present.  I installed network manager (or at least think I did).  I checked in Add/Remove programs and I see it listed as installed, but I can't find it anywhere.  The device manager shows the wireless card.  As per one person's suggestion I have enabled the universe/multiverse repositories, but still no luck.  What is really getting me with all this is someone from another forum said that this particular chipset won't work under linux on the powerbook.  ](*,) 
I noticed in the log that it identified my system as an i386.  Why is that?  Bottom line, have people with the Powerbook G4 been getting their bcm4318s (Airport Extreme?) to work?

I'm a longtime Windows end-user.  My background is healthcare so with the real technical stuff I might have some trouble, but I can usually follow directions okay.  :) 
I was excited to follow some steps that got my trackpad moving quickly as opposed to a snail's pace.  Now all I want to do is get my wireless up and running and I'll try to take care of anything else on my own (I got two Ubuntu books).  PLEASE if anyone can help straighten this out i would greatly appreciate it.  I would also hate to have to go out and buy a usb or pcmcia wireless card.  My partner at work (HUGE Windows fan) would really torture me then.  Thanks again.

Below are the contents of the bcm4318-setup.log from following the steps from the "how-to":

Log of echo Script version: 0.1.2 
Fri Jan 19 05:16:47 2007

Script version: 0.1.2

Fri Jan 19 05:16:47 2007
----------------
Log of lspci 
Fri Jan 19 05:16:47 2007

0000:00:0b.0 Host bridge: Apple Computer Inc. Intrepid2 AGP Bridge
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
0001:10:0b.0 Host bridge: Apple Computer Inc. Intrepid2 PCI Bridge
0001:10:11.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0001:10:14.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:15.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:15.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:15.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0002:24:0b.0 Host bridge: Apple Computer Inc. Intrepid2 PCI Bridge
0002:24:0d.0 Class ff00: Apple Computer Inc. Intrepid2 ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Computer Inc. Intrepid2 Firewire
0002:24:0f.0 Ethernet controller: Apple Computer Inc. Intrepid2 GMAC (Sun GEM)

Fri Jan 19 05:16:47 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Fri Jan 19 05:16:47 2007

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Fri Jan 19 05:16:47 2007
----------------
Log of cat /etc/issue 
Fri Jan 19 05:16:47 2007

Ubuntu 6.10 \n \l


Fri Jan 19 05:16:47 2007
----------------
Log of ps -e 
Fri Jan 19 05:16:47 2007

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
   29 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kseriod
   66 ?        00:00:00 pdflush
   67 ?        00:00:00 pdflush
   68 ?        00:00:00 kswapd0
   69 ?        00:00:00 aio/0
 1593 ?        00:00:00 khubd
 1601 ?        00:00:00 khpsbpkt
 1678 ?        00:00:00 knodemgrd_0
 1731 ?        00:00:01 kjournald
 1804 ?        00:00:00 logd
 1937 ?        00:00:00 udevd
 2673 ?        00:00:00 pccardd
 3317 ?        00:00:00 dhclient3
 3539 tty1     00:00:00 getty
 3540 tty2     00:00:00 getty
 3541 tty3     00:00:00 getty
 3542 tty4     00:00:00 getty
 3543 tty5     00:00:00 getty
 3544 tty6     00:00:00 getty
 3635 ?        00:00:00 dd
 3637 ?        00:00:00 klogd
 3658 ?        00:00:01 pbbuttonsd
 3777 ?        00:00:00 gdm
 3778 ?        00:00:00 gdm
 3798 tty7     00:00:54 Xorg
 3849 ?        00:00:00 cupsd
 3868 ?        00:00:00 hpiod
 3875 ?        00:00:00 python
 3915 ?        00:00:00 dbus-daemon
 3930 ?        00:00:02 hald
 3931 ?        00:00:00 hald-runner
 3938 ?        00:00:00 hald-addon-keyb
 3953 ?        00:00:00 hald-addon-keyb
 3974 ?        00:00:00 hald-addon-stor
 3982 ?        00:00:00 hald-addon-pmu
 4002 ?        00:00:00 perl
 4023 ?        00:00:00 powernowd
 4053 ?        00:00:00 hcid
 4059 ?        00:00:00 sdpd
 4067 ?        00:00:00 krfcommd
 4100 ?        00:00:00 atd
 4113 ?        00:00:00 cron
 4209 ?        00:00:03 x-session-manag
 4247 ?        00:00:00 ssh-agent
 4250 ?        00:00:00 dbus-launch
 4251 ?        00:00:00 dbus-daemon
 4253 ?        00:00:01 gconfd-2
 4259 ?        00:00:00 gnome-keyring-d
 4262 ?        00:00:00 gnome-settings-
 4279 ?        00:00:00 sh
 4280 ?        00:00:00 esd
 4295 ?        00:00:06 metacity
 4300 ?        00:00:13 gnome-panel
 4302 ?        00:00:03 nautilus
 4311 ?        00:00:00 gnome-vfs-daemo
 4317 ?        00:00:00 gnome-volume-ma
 4323 ?        00:00:02 update-notifier
 4325 ?        00:00:00 evolution-alarm
 4333 ?        00:00:00 gnome-cups-icon
 4349 ?        00:00:00 gnome-power-man
 4364 ?        00:00:00 mapping-daemon
 4366 ?        00:00:00 trashapplet
 4393 ?        00:00:00 mixer_applet2
 4462 ?        00:00:01 notification-da
 4556 ?        00:00:00 gnome-screensav
 4576 ?        00:00:00 dhclient3
 7967 ?        00:00:00 syslogd
11638 ?        00:00:42 firefox-bin
13249 ?        00:00:01 gnome-terminal
13251 ?        00:00:00 bonobo-activati
13259 ?        00:00:00 gnome-pty-helpe
13260 pts/0    00:00:00 bash
16770 pts/0    00:00:00 sh
16826 pts/0    00:00:00 logsave
16827 pts/0    00:00:00 ps

Fri Jan 19 05:16:47 2007
----------------
Log of echo Edgy final release detected. 
Fri Jan 19 05:16:47 2007

Edgy final release detected.

Fri Jan 19 05:16:47 2007
----------------
Log of rmmod ndiswrapper 
Fri Jan 19 05:16:47 2007

ERROR: Module ndiswrapper does not exist in /proc/modules
rmmod died with exit status 1

Fri Jan 19 05:16:47 2007
----------------
Log of rmmod bcm43xx 
Fri Jan 19 05:16:47 2007


Fri Jan 19 05:16:47 2007
----------------
Log of echo Edgy 
Fri Jan 19 05:16:47 2007

Edgy

Fri Jan 19 05:16:47 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Fri Jan 19 05:16:47 2007

Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package ndiswrapper-utils-1.8
apt-get died with exit status 100

Fri Jan 19 05:16:48 2007
----------------
Log of ndiswrapper -e bcmwl5 
Fri Jan 19 05:16:48 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Fri Jan 19 05:16:48 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Fri Jan 19 05:16:48 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Fri Jan 19 05:16:48 2007
----------------
Log of ndiswrapper -l 
Fri Jan 19 05:16:48 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Fri Jan 19 05:16:48 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Fri Jan 19 05:16:48 2007

You appear to have an i386 system...installing the i386 drivers...

Fri Jan 19 05:16:48 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Fri Jan 19 05:16:48 2007


Fri Jan 19 05:16:48 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Fri Jan 19 05:16:48 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Fri Jan 19 05:16:48 2007
----------------
Log of modprobe ndiswrapper 
Fri Jan 19 05:16:48 2007

FATAL: Module ndiswrapper not found.
modprobe died with exit status 1

Fri Jan 19 05:16:48 2007
----------------
Log of iwconfig 
Fri Jan 19 05:16:48 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Fri Jan 19 05:16:48 2007
----------------
Log of ifconfig 
Fri Jan 19 05:16:48 2007

eth0      Link encap:Ethernet  HWaddr 00:14:51:19:EF:06  
          inet addr:192.168.102.100  Bcast:192.168.102.255  Mask:255.255.255.0
          inet6 addr: fe80::214:51ff:fe19:ef06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172585805 (164.5 MiB)  TX bytes:4688189 (4.4 MiB)
          Interrupt:41 Base address:0x3800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)


Fri Jan 19 05:16:48 2007
----------------
Log of iwlist scan 
Fri Jan 19 05:16:48 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Fri Jan 19 05:16:49 2007
----------------

---

### Post by calum on 2007-01-19
Works for me, looks like you were maybe following the wrong instructions (maybe for a MacBook?)-- ndiswrapper is for using Windows drivers on x86 Linux machines, AFAIK, and won't help you on PPC.

On PPC, support is already in the kernel, you should just need to copy the firmware over to the appropriate directory from a Mac OSX install (using the fwcutter utility).  Search the forums for 'fwcutter airport extreme', you should find more detailed instructions.

---

### Post by Win2Mac2Linux on 2007-01-19
I wish someone had mentioned that previously.  Because I don't know any better, I was following instructions for my particular chipset, not realizing or thinking that there is a difference between the two platforms.  I had been listing that I had a Powerbook, but you are the first to mention this type of suggestion.  I can't deny people have been very helpful and quick at times to respond to posts, I just wish one of them had pointed this issue out.  Thank you for your help.  I will look into it and hopefully be up and running.

---

