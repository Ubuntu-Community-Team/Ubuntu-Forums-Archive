---
title: "BCM4318 Wireless Assistance Requested"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Bad Karma on 2007-03-01
Hello all! I know that there are countless threads on this issue already, and I have read several of them fairly thoroughly, but to no avail. I have a Compaq V5210US notebook, with a Broadcom 4318 Air Force One wireless chip, ATI Radeon Xpress 200M chipset, and Turion 64 ML-36 (?) processor. It is dual-booting with XP Professional. I cannot for the love of God get the wireless chip to enable. Last night, after running the ndiswrapper script through Terminal I was able to get the wireless light to come on, but nothing would show for wireless devices in Networking. Today, I restarted and tried to rerun the script, to no avail. Now the bloody light won't even turn on. Here is a copy of the log, fair warning, its long:

Log of echo Script version: 0.1.2 
Thu Mar  1 10:55:22 2007

Script version: 0.1.2

Thu Mar  1 10:55:22 2007
----------------
Log of lspci 
Thu Mar  1 10:55:22 2007

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Thu Mar  1 10:55:22 2007
----------------
Log of echo /etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e 
Thu Mar  1 10:55:22 2007

/etc/issue MD5 sum: 11046fbe3787d2ba4fc5821d5a41617e

Thu Mar  1 10:55:22 2007
----------------
Log of cat /etc/issue 
Thu Mar  1 10:55:22 2007

Ubuntu 6.10 \n \l


Thu Mar  1 10:55:22 2007
----------------
Log of ps -e 
Thu Mar  1 10:55:22 2007

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   98 ?        00:00:00 kseriod
  131 ?        00:00:00 pdflush
  132 ?        00:00:00 pdflush
  133 ?        00:00:00 kswapd0
  134 ?        00:00:00 aio/0
 1698 ?        00:00:00 khubd
 1782 ?        00:00:00 kjournald
 1855 ?        00:00:00 logd
 2001 ?        00:00:00 udevd
 2760 ?        00:00:00 kpsmoused
 2832 ?        00:00:00 shpchpd
 3503 tty1     00:00:00 getty
 3504 tty2     00:00:00 getty
 3505 tty3     00:00:00 getty
 3506 tty4     00:00:00 getty
 3507 tty5     00:00:00 getty
 3508 tty6     00:00:00 getty
 3740 ?        00:00:00 acpid
 3854 ?        00:00:00 dd
 3856 ?        00:00:00 klogd
 3930 ?        00:00:00 gdm
 3931 ?        00:00:00 gdm
 3950 tty7     00:00:07 Xorg
 3968 ?        00:00:00 cupsd
 3985 ?        00:00:00 hpiod
 3988 ?        00:00:00 python
 4036 ?        00:00:00 dbus-daemon
 4053 ?        00:00:01 hald
 4054 ?        00:00:00 hald-runner
 4060 ?        00:00:00 hald-addon-acpi
 4066 ?        00:00:00 hald-addon-keyb
 4090 ?        00:00:00 hald-addon-stor
 4110 ?        00:00:00 perl
 4150 ?        00:00:00 ondemand
 4189 ?        00:00:00 hcid
 4196 ?        00:00:00 sdpd
 4206 ?        00:00:00 krfcommd
 4226 ?        00:00:00 anacron
 4240 ?        00:00:00 atd
 4253 ?        00:00:00 cron
 4378 ?        00:00:00 x-session-manag
 4413 ?        00:00:00 ssh-agent
 4416 ?        00:00:00 dbus-launch
 4417 ?        00:00:00 dbus-daemon
 4419 ?        00:00:00 gconfd-2
 4422 ?        00:00:00 gnome-keyring-d
 4425 ?        00:00:00 gnome-settings-
 4441 ?        00:00:00 sh
 4442 ?        00:00:00 esd
 4449 ?        00:00:01 metacity
 4454 ?        00:00:02 gnome-panel
 4456 ?        00:00:02 nautilus
 4460 ?        00:00:00 bonobo-activati
 4462 ?        00:00:00 gnome-volume-ma
 4466 ?        00:00:00 gnome-vfs-daemo
 4472 ?        00:00:00 update-notifier
 4477 ?        00:00:00 evolution-alarm
 4483 ?        00:00:00 gnome-cups-icon
 4486 ?        00:00:00 gnome-power-man
 4508 ?        00:00:00 trashapplet
 4521 ?        00:00:00 mapping-daemon
 4534 ?        00:00:00 mixer_applet2
 4540 ?        00:00:00 gnome-netstatus
 4556 ?        00:00:00 gnome-screensav
 4566 ?        00:00:00 dhclient3
 5308 ?        00:00:00 syslogd
 5479 ?        00:00:00 wrap_wq
 5480 ?        00:00:00 ndis_wq
 5545 ?        00:00:00 sh
 5546 ?        00:00:00 run-parts
 5550 ?        00:00:00 scrollkeeper
 5551 ?        00:00:00 scrollkeeper-re
 5557 ?        00:00:55 scrollkeeper-up
 6294 ?        00:00:00 gnome-terminal
 6297 ?        00:00:00 gnome-pty-helpe
 6298 pts/0    00:00:00 bash
 6493 pts/0    00:00:00 sh
 6561 pts/0    00:00:00 logsave
 6562 pts/0    00:00:00 ps

Thu Mar  1 10:55:22 2007
----------------
Log of echo Edgy final release detected. 
Thu Mar  1 10:55:22 2007

Edgy final release detected.

Thu Mar  1 10:55:22 2007
----------------
Log of rmmod ndiswrapper 
Thu Mar  1 10:55:22 2007


Thu Mar  1 10:55:22 2007
----------------
Log of rmmod bcm43xx 
Thu Mar  1 10:55:22 2007

ERROR: Module bcm43xx does not exist in /proc/modules
rmmod died with exit status 1

Thu Mar  1 10:55:22 2007
----------------
Log of echo Edgy 
Thu Mar  1 10:55:22 2007

Edgy

Thu Mar  1 10:55:22 2007
----------------
Log of apt-get --assume-yes install ndiswrapper-common ndiswrapper-utils-1.8 
Thu Mar  1 10:55:22 2007

Reading package lists...
Building dependency tree...
Reading state information...
E: Couldn't find package ndiswrapper-common
apt-get died with exit status 100

Thu Mar  1 10:55:22 2007
----------------
Log of ndiswrapper -e bcmwl5 
Thu Mar  1 10:55:22 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Thu Mar  1 10:55:22 2007
----------------
Log of ndiswrapper -e bcmwl5a 
Thu Mar  1 10:55:22 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Thu Mar  1 10:55:22 2007
----------------
Log of ndiswrapper -l 
Thu Mar  1 10:55:22 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Thu Mar  1 10:55:22 2007
----------------
Log of echo You appear to have an i386 system...installing the i386 drivers... 
Thu Mar  1 10:55:22 2007

You appear to have an i386 system...installing the i386 drivers...

Thu Mar  1 10:55:22 2007
----------------
Log of tar -xf drivers-32.tar.gz 
Thu Mar  1 10:55:22 2007


Thu Mar  1 10:55:22 2007
----------------
Log of ndiswrapper -i bcmwl5.inf 
Thu Mar  1 10:55:22 2007

ndiswrapper: No such file or directory
ndiswrapper died with exit status 1

Thu Mar  1 10:55:22 2007
----------------
Log of modprobe ndiswrapper 
Thu Mar  1 10:55:22 2007


Thu Mar  1 10:55:22 2007
----------------
Log of iwconfig 
Thu Mar  1 10:55:22 2007

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


Thu Mar  1 10:55:22 2007
----------------
Log of ifconfig 
Thu Mar  1 10:55:22 2007

eth0      Link encap:Ethernet  HWaddr 00:16:D4:40:FE:AA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10132 (9.8 KiB)  TX bytes:10132 (9.8 KiB)


Thu Mar  1 10:55:22 2007
----------------
Log of iwlist scan 
Thu Mar  1 10:55:22 2007

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.


Thu Mar  1 10:55:22 2007
----------------


Well, being COMPLETELY new to *nix systems in general (long-time windows enthusiast finally sent over the edge by Vista), I have no clue what to make of this log, or how to get this card to work. I'm almost tempted to just go buy a wireless PCMCIA NIC for it. I'd like to avoid that route, but if I must does anyone know of any good Express Card wireless chips or USB wireless chips that play nice with Edgy?

---

### Post by Mizled on 2007-03-01
This is the guide I used for my Broadcom 4306 integrated card with my HP notebook.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

---

### Post by lavinog on 2007-03-04
I have a similar laptop: v5206 
I got it to work on both 32 and 64 bit edgy
it was a matter of finding the right drivers to use with ndiswrapper, (and doing the other things like blacklisting bcm43xx)
The driver that came with windows did not work for me.
To get the 32 bit drivers to work I used this page: 
[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218]("http://ubuntuforums.org/showpost.php?p=1105667&postcount=218")
and used the driver provided on that page. I think one thing i had to do different was install ndiswrapper-utils-1.8 on step 3 instead of just ndiswrapper-utils which is a older version

I recently broke the 64 bit wireless. If you need that info give me some time.

---

### Post by Kobalt on 2007-03-04
You guys shouls head [over there]("http://www.ubuntuforums.org/showthread.php?t=197102") : there's a script that makes it all for you, including getting the right drivers.

---

### Post by lavinog on 2007-03-04
> **Kobalt said:**
> You guys shouls head [over there]("http://www.ubuntuforums.org/showthread.php?t=197102") : there's a script that makes it all for you, including getting the right drivers.

> If you are using 64bit Edgy Eft and the 2.6.17-10-generic, make sure you are NOT using the 2.6.17-10-generic kernel as it doesn't work

According to that page it doesn't work with 2.6.17-10
and it doesn't seem to work with 2.6.17-11 either (or something else is wrong)

I had mine working with 2.6.17-10 and i think it was just a matter of using a different version of bcmwl564

---

### Post by pearlie on 2007-03-04
[This method]("https://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5") worked for me on my V5000... well, mostly, anyway - I could get my light to come on, but I still couldn't configure my wireless through wifi radar or the default network manager.  So  I went [here]("http://compwiz18.blackhole.cx/wicd/wb/") and downloaded Wicd, configured it with my WEP key, and voila! wireless works now.

---

