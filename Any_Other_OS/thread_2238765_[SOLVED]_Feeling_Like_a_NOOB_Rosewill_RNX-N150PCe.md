---
title: "[SOLVED] Feeling Like a NOOB: Rosewill RNX-N150PCe"
date: 2014-08-09
forum: Any Other OS
---

### Post by Wolfie Lee on 2014-08-09
Ok I really looked but after all the modprobing and running diagnostics shown on page one here:

[http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)

It just keeps throwin' these dang trees in the road! I can see a great many things that really concern me, but just can't make any use of knowing these concerns are legit. That thread is an 11 pager and has no [solved] tagged to it, and my eyes were 'bout ready to fall outtta my head, so I apologize for the need of hand -holding. Well,  anyway...here is the last probe output:

```
brucelee@brucelee-desktop:~$ sudo modprobe rt3562sta
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
brucelee@brucelee-desktop:~$ sudo ifconfig ra0 inet up
ra0: ERROR while getting interface flags: No such device
brucelee@brucelee-desktop:~$ 
```


and I have MANY concerns about the Diagnostic script output:

```

########## wireless info START ##########

Report from: 09 Aug 2014 20:31 EDT -0400

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.4 LTS
Release:	10.04
Codename:	lucid

##### kernel #####

Linux 2.6.32-64-generic #128-Ubuntu SMP Tue Jul 15 08:32:40 UTC 2014 x86_64 unknown unknown GNU/Linux

Parameters: ro, quiet, splash

##### desktop #####

GNOME

##### lspci #####

03:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169

##### lsusb #####

Bus 002 Device 003: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 002: ID 0b38:0003  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 002: ID 0bc2:50a5 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

ndiswrapper           244832  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.254.24  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:feed:b253/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39039735 (39.0 MB)  TX bytes:2913741 (2.9 MB)
          Interrupt:27 Base address:0x4000 

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 eth0

##### resolv.conf #####

domain netgear.com
search netgear.com
nameserver 192.168.254.254

##### nm-tool #####

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.254.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.254.254

    DNS:             192.168.254.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf #####

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

nm-system-settings.conf (used up to Ubuntu 10.04):

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### iw reg get #####

./wireless_script: line 138: iw: command not found

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #####

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos #####

[ndiswrapper]
filename:       /lib/modules/2.6.32-64-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
license:        GPL
version:        1.55
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DBEE4C88A248D81731F20F7
depends:        
vermagic:       2.6.32-64-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #####

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules #####

lp
rtc

##### blacklists #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   25.551251] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   25.610820] type=1505 audit(1407628946.345:3):  operation="profile_load" pid=702 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.184170] type=1505 audit(1407628946.925:7):  operation="profile_replace" pid=945 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

########## wireless info END ############
```

The only other time I needed wireless help was with a generic dongle that worked GREAT in Fiesty, but after a wipe and fresh install of Gnatty, went dead. I am now recently moved into a nice studio apt. and want my Box across the room from the phone jack. This thing works great in windows, after a bit of  struggle, and it still shows "no internet connection", but it is lying...lol. However, I ALWAYS severely restrict the time I give Windows in "The REAL World".

Any help would be greatly appreciated!

Thanx!

---

### Post by chili555 on 2014-08-10
Ubuntu 10.04 is very far past its end-of-life. We suggest you upgrade to at least 12.04 LTS. We have made a lot of progress in wireless drivers in 4 1/2 years! As an example, the built-in wireless device works well in later Ubuntu versions.

---

### Post by Wolfie Lee on 2014-08-10
Yeah...I have been conditioning myself to give it up. I REALLY do not like not being able to customize my toolbars. Why would Unity take all the customizing out of your desktop environment? Can't even make a quick launch button!?! Not to mention the no support issues that I believe have been creepin' in here, lately. I will be upgrading to an FX9xxx series cpu, and and an MSI MB with USB 3.0 and SATA 3, a Samsung 840 pro SSD 256GB OS drive, not to mention, a Blu-Ray Burner...LOL I AM very far behind the times! I know there are no Haters here, but I actually am running Ultimate Edition 2.7 (based on Lucid), and they are at about 4.9 or some such now with the Latest UBU kernel....So I'll be changing OS's when I change to the new build. I guess the box will have to just be tied to it's present location 'till I can get it done.... the first parts (excluding this Wireless card) will be arriving by the end of the week....but my budget will keep the parts at a trickle for at least 1 1/2 to 3 Months, or so.

SOooo....are those outputs totally fried or what!??...LOL

Thanks for the reply, but it has been coming down to the upgrade issue now for quite some time. It shall be done.

Later, Wolfie....

---

### Post by chili555 on 2014-08-10
> I REALLY do not like not being able to customize my toolbars. Why would Unity take all the customizing out of your desktop environment?There are plenty of ways to not use Unity; kubuntu, xubuntu and lubuntu for example. I suggest you try the live DVD and, if you like it, install.> SOooo....are those outputs totally fried or what!??Hard to tell, I don't even see the wireless device in question. > Not to mention the no support issues that I believe have been creepin' in here, lately. That means that security flaws will no longer be addressed. I suppose that's just fine if you only play solitaire on your computer, but if you ever put in a password, credit card number or other personal information, it's a big problem and one that hackers love to exploit: computers without security updates and, therefore, known exploitable holes.

I am disinclined to fix a flawed Ubuntu version.

---

### Post by howefield on 2014-08-10
Thread moved to the "Other Operating Systems and Projects" forum.

---

### Post by Wolfie Lee on 2014-08-10
Yeah, I have the newest Ulitimate Edition on a Live USB right now but for some STRANGE reason, I can't LOGIN to the Live session, because it asks for a username and password! Gotta get to the UE forums on that and get that user/pass info, I guess, but I have not heard of or encountered this before...been outta the loop with no internet now for over 2 years...

Sorry, howefield, thanks for the placement help....

oh yeah....forgot it's an Asus M5A97 R2.0 MB (not the MSI I THOUGHT I had it boiled down to)...it is the first major part on it's way from ebay now...got an Open Box deal with no I/O plate....MAN I can't wait!

---

### Post by Wolfie Lee on 2014-08-10
OK, I still can't Login, and am awaiting response on that issue, but even at the login screen, the new OS was Rockin' the wireless! Very sweet!

Gusess we'll call this SOLVED...too much headache to try and muddle through it all when I will have the new Ultimate Edition on it's own partition, soon...

Then I'll login to Kubuntu and see to the customization issue I thought I would never be able to get past...Thanks, chilli555! 

Have a Great Day, all!

---

