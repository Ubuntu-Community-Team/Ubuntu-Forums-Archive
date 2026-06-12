---
title: "Powerbook G4 12&quot;"
date: 2007-09-02
forum: Apple PPC Users
---

### Post by nullsleep on 2007-09-02
well i have a powerbook G4 and i am trying to get ubuntu installed on it, i am kind of new to ubuntu i have it on my intel laptop but want to try it on my powerbook, i have downloaded the ISO and burned it, it boots but then kickes me to the initramfs fallback, no GUI, i cant even see the HDD or CD, any one knows whats going on?

---

### Post by tgalati4 on 2007-09-02
Do you have at least 256 MB of RAM?

---

### Post by stmiller on 2007-09-02
Which version of Ubuntu? Try Feisty, the newest version. It is not listed on the ubuntu.com download section for some reason, but here is a link:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by nullsleep on 2007-09-02
well i am using the newist version i can find and that is feisty and yes i have more than 256MB, i have 512MB installed, but now i am installing Gentoo as thats the only one i can get to boot

---

### Post by yey365 on 2007-09-02
Forgive me if this is a silly question but did you download the ppc version?  Or are you trying to install the Intel version?

---

### Post by nullsleep on 2007-09-02
i have downloaded the PPC version

---

### Post by jsonder on 2007-09-02
I think that I did an upgrade with Feisty, but did the original installation with 6.06 or 6.10 on my mac mini.

Are you trying to do a dual boot or a "wipe the hard drive" install?

If dual boot, you need the new world stuff.  I'll have to shift from my old core duo notebook and boot my G4 mini if you need more on this.

---

### Post by nullsleep on 2007-09-02
well i am trying to dual boot, got it working with Gentoo now, but whould like ubuntu as i like ubuntu on laptops but gentoo on desktops

---

### Post by jsonder on 2007-09-02
Here's a link to the gparted lay out of my mini's drive:

[http://members.cox.net/so4plume/drives.jpg](http://members.cox.net/so4plume/drives.jpg)

The last 3 partitions are the Ubuntu ones (swap, /  and everything but /home, and /home)

You need to use yaboot and have the New World files installed in either #1 or the un-nunbered, un-named piece.

#2 and #3 are the boot and OSX partitions.  I think that during the partitioning process (while installing the PPC version of Ubuntu) I actually had 8 partitions, with the 1st 5 being mac related.  Obviously, one is lost and one is now unnumbered.

OSX kept for video purposes (quicktime and movies) and for the youngest kid to use when he visits.

---

### Post by nullsleep on 2007-09-02
thank you for that, but i still cant get ubuntu CD to boot, i have gentoo installed now and thats up and running with gnome just trying to get the airport working now, it is dual booting fine with OS X, but i would like ubuntu on it but i cba to find out why its not even booting the install cd as i have gentoo working, if some one has some thing i could try or some thing then please say. 

as for my HD layout, i havent a clue, i know hda4 is linux root hda5 is swap and hda8 is OS X

---

### Post by jsonder on 2007-09-02
I used a 6.06 "Desktop" and 6.10 and 7.04 Alternate Install versions, but I think the initial installation was from Flight 5 of Dapper Dan ( 5th alpha/beta of 6.06).  I'm sure that I had to hold or tap the c key to get it to boot from the cd.

---

### Post by nullsleep on 2007-09-03
i know you have to hold the C key to get it to boot from CD but i have yaboot installed with a boot from cd option, i have downloaded a load of old versions are none seem to work

---

### Post by pxwpxw on 2007-09-03
**nullsleep**

When you get the yaboot menu prompt "boot: " 

TAB for a list of options.
Try these

live-nosplash
check

If no progress, trash the Desktop CD (it just makes bug finding impossible)
Get the Alternate CD, no desktop to confuse the issue.

---

### Post by nullsleep on 2007-09-03
well i have tryed all that and the desktop and Alternate CD, all i get is the initramfs fall back and nothing else.

---

### Post by pxwpxw on 2007-09-03
What are the last few lines messages you see from the initramfs screen?

---

### Post by nullsleep on 2007-09-03
i cant remeber what but i do know that there is only 2 lines and they where not errors, will boot it to find out what it said.

---

### Post by nullsleep on 2007-09-03
right i have ubuntu booting now and all i did was put it on CDRW and not a CDR funny powerbook

booting Ubuntu 7.04 with live-nosplash-powerpc

---

### Post by pxwpxw on 2007-09-03
Good.  Have fun.

---

### Post by nullsleep on 2007-09-03
right have it installed now but cant get it to conect to my wireless net, it can see it, there are not errors in the dmesg, i have searched the forum and nothing has helped

this is all i get in dmesg 
SoftMAC: Open Authentication completed with 00:14:bf:93:3d:c4
ADDRCONF(NETDEV_UP): eth1: link is not ready

and thats it

---

### Post by pxwpxw on 2007-09-04
**nullsleep**

have you configured your network  and done a full restart. ( From the desktop using the network manager (dont know its exact name for ubuntu, I have xubuntu here, its just Applications:System:Network)

If you did that and still nogo, can you post text output from

```

 lsmod | grep bcm
 ifconfig
 iwconfig
 cat /etc/network/interfaces

```

---

### Post by nullsleep on 2007-09-04
```
nullsleep@nullsleep-powerbook:~$ lsmod | grep bcm43xx
bcm43xx               143316  0 
ieee80211softmac       35040  1 bcm43xx
ieee80211              35653  2 bcm43xx,ieee80211softmac
```

```
nullsleep@nullsleep-powerbook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0D:93:3D:C9:90  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:93ff:fe3d:c990/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1718780 (1.6 MiB)  TX bytes:230297 (224.8 KiB)
          Interrupt:41 Base address:0x9000 

eth1      Link encap:Ethernet  HWaddr 00:11:24:23:C2:2D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:14293 (13.9 KiB)
          Interrupt:52 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```


```
nullsleep@nullsleep-powerbook:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"nullnet"  Nickname:"nullnet"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


```
nullsleep@nullsleep-powerbook:~$ cat /etc/networks/interfaces
cat: /etc/networks/interfaces: Not a directory

```

i do have a /etc/networks so here it is if its any help
```
nullsleep@nullsleep-powerbook:~$ cat /etc/networks 
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0

```

oo and i found the one you might of ment cat /etc/network/interfaces

```
nullsleep@nullsleep-powerbook:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


```

---

### Post by pxwpxw on 2007-09-04
OK, sorry about the networks typo.

You seem to have the default madwifi drivers, which are for some of the intel macs.
What do you get from
```

lsmod | grep ath
ls -l /lib/firmware

```
You probably need bcm43xx-fwcutter or other package for bcm43xx firmware, or else ndiswrapper.

Edit:
and just to make sure
```

lspci
### the wireless net controller Broadcom??

```

---

### Post by nullsleep on 2007-09-05
```
oot@ubuntu:/home/ubuntu# lsmod | grep ath
root@ubuntu:/home/ubuntu# ls -l /lib/firmware
total 132
drwxr-xr-x 4 root root  1549 2007-04-15 13:48 2.6.20-15-powerpc
drwxr-xr-x 4 root root  1540 2007-04-15 13:48 2.6.20-15-powerpc64-smp
-rw-r--r-- 1 root root  3504 2007-09-05 13:29 bcm43xx_initval01.fw
-rw-r--r-- 1 root root    16 2007-09-05 13:29 bcm43xx_initval02.fw
-rw-r--r-- 1 root root  3504 2007-09-05 13:29 bcm43xx_initval03.fw
-rw-r--r-- 1 root root    16 2007-09-05 13:29 bcm43xx_initval04.fw
-rw-r--r-- 1 root root  2536 2007-09-05 13:29 bcm43xx_initval05.fw
-rw-r--r-- 1 root root   248 2007-09-05 13:29 bcm43xx_initval06.fw
-rw-r--r-- 1 root root  2536 2007-09-05 13:29 bcm43xx_initval07.fw
-rw-r--r-- 1 root root  2536 2007-09-05 13:29 bcm43xx_initval08.fw
-rw-r--r-- 1 root root   248 2007-09-05 13:29 bcm43xx_initval09.fw
-rw-r--r-- 1 root root   248 2007-09-05 13:29 bcm43xx_initval10.fw
-rw-r--r-- 1 root root 21672 2007-09-05 13:29 bcm43xx_microcode11.fw
-rw-r--r-- 1 root root 16352 2007-09-05 13:29 bcm43xx_microcode2.fw
-rw-r--r-- 1 root root 20088 2007-09-05 13:29 bcm43xx_microcode4.fw
-rw-r--r-- 1 root root 22272 2007-09-05 13:29 bcm43xx_microcode5.fw
-rw-r--r-- 1 root root  1312 2007-09-05 13:29 bcm43xx_pcm4.fw
-rw-r--r-- 1 root root  1312 2007-09-05 13:29 bcm43xx_pcm5.fw
```

```
root@ubuntu:/home/ubuntu# lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

```

---

### Post by pxwpxw on 2007-09-05
Well, looks like all the drivers and firmware is there for the  Airport card. Have you set up the Network in your desktop aplications. Are you using WEP or WAP security - that might need something extra.

and have you got macosx using wireless.

---

### Post by nullsleep on 2007-09-05
i am using WPA but have switched to wep and no security and the same thing.

---

### Post by pxwpxw on 2007-09-05
But what about the Network manager have you done that?

---

### Post by nullsleep on 2007-09-05
network-manager sees my network and it comes up asking for the password i enter that and it just sits there doing nothing, no errors, it just doesnt connect

---

### Post by pxwpxw on 2007-09-06
> **nullsleep said:**
> network-manager sees my network and it comes up asking for the password i enter that and it just sits there doing nothing, no errors, it just doesnt connect

Right, well I don't think I can go much further with this, because I have xubuntu here, with its own version of network manager just using WEP, and unless you also have xubuntu 704, it will not be the same as yours, and I will only confuse you, but if you have xubuntu I can carry on a bit further, but I am not a wireless expert by any means.  

If not, I think you might need to start a new thread about help for help with  wireless network manager, there are several alternative network manager options available.

The info you have posted here is all relevant.

---

### Post by nullsleep on 2007-09-07
ok, will do, i am going to try xubuntu as i have never tryed it and yes i have use XFCE as thats what i use on my Xbox and old laptop, well get back to you if the prob is still there with xubuntu

---

### Post by ibbumpin on 2007-09-07
I'ave always used wifi-radar after installing the wireless drivers.  I could never get network-manager to work and wifi-radar just worked for me.  Might be worth trying before doing a complete reinstall.

---

### Post by nullsleep on 2007-09-08
well ibbumpin, i have just tryed wifi-radar and agen it just will not connect, no encription, wep or wpa made a dif it just would not connect, i have tryed to do it all from the cli and the same it seemed to connect then it would just disconnect. i know when i was using gentoo that would come up with a 0x13 error

---

