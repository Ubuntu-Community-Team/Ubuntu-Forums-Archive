---
title: "Hi... please help with wireless..."
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Nnako2 on 2008-02-16
Hi everyone...

I'm Spanish so sorry if my English is bad, but I need your help 8-[



I had lots of problems with installing Ubuntu 7.10 having Windows Vista at the same PC, but I finally could.


But at the moment I'm at my Windows... That's because I couldn't connect to any wireless with Ubuntu yet.


First of all:
- I'm very very newbie at this stuff, please explain as simple as possible. I'll do all I can, thanks a lot. Don't use difficult English, please, I need explanations for children :(
- I know there are lots of threads like this in the Internet, I've searched and I've tried but nothing works to me.



My PC is an HP laptop.

At Windows I used to connect to the Internet with a wireless connection from a router connected to another PC with Windows XP.

The router is a Belkin 54g and I need to use it for both PCs, for Windows and Ubuntu.



The matter is that I don't know how to connect to the Internet with Ubuntu. I've never done it but with Windows and I don't know what's normal and what's wrong with my Ubuntu. I write my SSID and WAP password at wireless connections but nothing ever happens and I wonder why... :lol:

I've tried to change things from my router at 192.168.2.1 but nothing happens again. It seems as Ubuntu doesn't recognize any connections, any wireless connections, and Windows usually finds mine, the neighbourd's, and much more... but Ubuntu doesn't.

---

### Post by Nnako2 on 2008-02-16
Hi everyone...

I'm Spanish so sorry if my English is bad, but I need your help 8-[



I had lots of problems with installing Ubuntu 7.10 having Windows Vista at the same PC, but I finally could.


But at the moment I'm at my Windows... That's because I couldn't connect to any wireless with Ubuntu yet.


First of all:
- I'm very very newbie at this stuff, please explain as simple as possible. I'll do all I can, thanks a lot. Don't use difficult English, please, I need explanations for children :(
- I know there are lots of threads like this in the Internet, I've searched and I've tried but nothing works to me.



My PC is an HP laptop.

At Windows I used to connect to the Internet with a wireless connection from a router connected to another PC with Windows XP.

The router is a Belkin 54g and I need to use it for both PCs, for Windows and Ubuntu.



The matter is that I don't know how to connect to the Internet with Ubuntu. I've never done it but with Windows and I don't know what's normal and what's wrong with my Ubuntu. I write my SSID and WAP password at wireless connections but nothing ever happens and I wonder why... :lol:

I've tried to change things from my router at 192.168.2.1 but nothing happens again. It seems as Ubuntu doesn't recognize any connections, any wireless connections, and Windows usually finds mine, the neighbourd's, and much more... but Ubuntu doesn't.

---

### Post by Nnako2 on 2008-02-16
Here you have some screenshots of what happens to me:

The matter is that when I write my SSID, I can't choose anyone, there are no SSIDs to choose, I have to write it manual and it seems as it doesn't find anyone, and when I "connect" my wireless it doesn't recognize anything and nothing happens... I don't know, I hope you will help me.

[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_0a23f3fb.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/0a23f3fb.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_afa4b73c.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/afa4b73c.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_fd8567c5.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/fd8567c5.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_5e6bf782.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/5e6bf782.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_8bb775d2.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/8bb775d2.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_1a928ee2.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/1a928ee2.png)
[[img]http://i27.photobucket.com/albums/c181/Nnako2/th_8c1cc468.png[/img]](http://i27.photobucket.com/albums/c181/Nnako2/8c1cc468.png)

---

### Post by Nnako2 on 2008-02-16
Anyway, since this below, I've been told that my wifi card is recognized  :roll: 

ubuntu@ubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
10:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1A:4B:62:74:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2400 (2.3 KB)  TX bytes:2400 (2.3 KB)

ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0




I've also tried this but I can't scan...


paula@paula-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4311"
Mode:Managed Access Point: Invalid
RTS thr:off Fragment thr:off
Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

paula@paula-laptop:~$ sudo iwlist eth1 scan
[sudo] password for paula:
eth1 Interface doesn't support scanning : No such device

paula@paula-laptop:~$ sudo iwlist eth1 scan
eth1 Interface doesn't support scanning : No such device

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 






Thanks a lot, I'm anxious to try the whole Ubuntu and forget about Windows!! :D

---

### Post by mikeyphi on 2008-02-16
If you can get a wired Internet connection then : open System/Administration/Restricted Drivers Manager and install the driver for your Broadcom hardware

---

### Post by jan quark on 2008-02-16
see my small tutorial on the broadcom 4311
you can download the files in xp and fetch them over to ubuntu
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

but I must say this card is very problematic on linux

---

### Post by Nnako2 on 2008-02-16
> **jan quark said:**
> see my small tutorial on the broadcom 4311
you can download the files in xp and fetch them over to ubuntu
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

but I must say this card is very problematic on linux



I'm unable to install it, I can't click Install Package, there's an error.

---

### Post by Nnako2 on 2008-02-16
> **Nnako2 said:**
> I'm unable to install it, I can't click Install Package, there's an error.


This is what I mean:

[[IMG]http://i27.photobucket.com/albums/c181/Nnako2/th_d9da56ee.png[/IMG]](http://i27.photobucket.com/albums/c181/Nnako2/d9da56ee.png)


and...

[[IMG]http://i27.photobucket.com/albums/c181/Nnako2/th_e9c827fc.png[/IMG]](http://i27.photobucket.com/albums/c181/Nnako2/e9c827fc.png)
[[IMG]http://i27.photobucket.com/albums/c181/Nnako2/th_b0b69731.png[/IMG]](http://i27.photobucket.com/albums/c181/Nnako2/b0b69731.png)
[[IMG]http://i27.photobucket.com/albums/c181/Nnako2/th_4fd50a8f.png[/IMG]](http://i27.photobucket.com/albums/c181/Nnako2/4fd50a8f.png)

---

### Post by Nnako2 on 2008-02-17
Please I need help!!!!

---

### Post by anewguy on 2008-02-17
Do you have the ability to hard-wire your connection to the router?  If so, we can give you instructions to get this going, but it does require an internet connection.:)

---

### Post by Nnako2 on 2008-02-17
> **anewguy said:**
> Do you have the ability to hard-wire your connection to the router?  If so, we can give you instructions to get this going, but it does require an internet connection.:)
No... I can't connect this PC with wire connection, I only can bring things with an pen drive...

---

### Post by ugm6hr on 2008-02-17
> **Nnako2 said:**
> No... I can't connect this PC with wire connection, I only can bring things with an pen drive...

Assuming this is correct: [http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

You have to manually download all the **dependencies** and install them in order.

[http://packages.ubuntu.com/gutsy/base/libc6](http://packages.ubuntu.com/gutsy/base/libc6)

Follow this link and go to the correct "Architecture" you have (likely [i386]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.6.1-1ubuntu9_i386.deb&md5sum=80a83b2d81477a6b78664c299ed5d1dd&arch=i386&type=main") if you have the "standard" Personal Computer Ubuntu, [amd64]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.6.1-1ubuntu9_amd64.deb&md5sum=89091b262d2be94a18d272b5951c31c8&arch=amd64&type=main") if you have the 64-bit version).  

Then select a mirror to download from.  Then, once downloaded, double-click the downloaded libc6 .deb

If it complains about any other dependencies - just download and double-click them as well - you should be able to find them linked from the above page as well.

Then the tutorial should work without complaint.

---

### Post by Nnako2 on 2008-02-17
Well.. I already had  libc6 and it happened the same to me... BUUUUT, the problem was bcm43xx-fwcutter_006-4_i386.deb, i was unable to install it but I tried to install another file: bcm43xx-fwcutter_20060108-6build1_i386 and it worked!!!!

Now I'm writting from my Ubuntu :D thanks everybody!!!!

---

### Post by jan quark on 2008-02-17
yes there is a problem with the versions of fwcutter

for me also not every version works at first

but I am glad my small tutorial helped somebody ;)

---

### Post by rustybronco on 2008-02-17
Glad you did it!!!!!

---

### Post by Nnako2 on 2008-02-17
> **jan quark said:**
> yes there is a problem with the versions of fwcutter

for me also not every version works at first

but I am glad my small tutorial helped somebody ;)
Of course it helped me!!

Thanks a lot! I'm so happy :D

---

### Post by Nnako2 on 2008-02-17
> **rustybronco said:**
> Glad you did it!!!!!
Thanks rustybronco for everything too!!!! I'm sorry I'm very impatiente

---

### Post by rustybronco on 2008-02-17
> **Nnako2 said:**
>  I'm sorry I'm very impatienteWhich never is a  never a prroblem with me.

---

### Post by stolid_agnostic on 2008-02-28
> **jan quark said:**
> see my small tutorial on the broadcom 4311
you can download the files in xp and fetch them over to ubuntu
[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

but I must say this card is very problematic on linux

I got a new compaq presario c500 with the BCM94311MCG card in it. For the most part, your mini tutorial  seems to have worked for me. I had to use this version of the cutter:

bcm43xx-fwcutter_20060501-5_i386.deb

as the newer one (6) wouldn't work for me.

When I run a:

iwlist scanning

I get:


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:4D:8D:62:0E
                    ESSID:"ATHOME"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=96/100  Signal level=-43 dBm  Noise level=-70 dBm
                    Extra: Last beacon: 28ms ago

...... (many others)

so it seems that the interface is working. However, when I run:

dhclient eth1

I get this:

There is already a pid file /var/run/dhclient.pid with pid 6921 [PRESUMABLY FROM THE ONE MY WIRED INTERFACE GOT]
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1a:73:39:a0:48
Sending on   LPF/eth1/00:1a:73:39:a0:48
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Any ideas on why the card would 'seem' to work but not actually take an IP for me?

Thanks!

---

