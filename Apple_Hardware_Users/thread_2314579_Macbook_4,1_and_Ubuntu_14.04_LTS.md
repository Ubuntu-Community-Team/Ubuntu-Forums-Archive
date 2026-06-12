---
title: "Macbook 4,1 and Ubuntu 14.04 LTS"
date: 2016-02-22
forum: Apple Hardware Users
---

### Post by ludovico_lorello on 2016-02-22
Hello to everybody, I just installed ubuntu 14.04 lts on my macbook 4,1.
After a lot of troubles with the partitions I finally reached the end.
Now, Ubuntu works fine but I have some BIG questions for you.

How do I know which drivers do I miss?
How can I test that ubuntu work properly?
Where do I find all drivers of my macbook?

I`m a beginner so I have very less experience.[INDENT]Thank you for help.
[/INDENT]

---

### Post by christiaan3 on 2016-02-23
First you can check which drivers are installed already with the command: **lspci**. To find the drivers you should have installed I advice you to lookup your hardware and find your drivers that way. Basically if your Ubuntu is working fine its alright. I mean when you installed your drivers and you're able to ping everywhere you want, you should be good.

---

### Post by howefield on 2016-02-23
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ludovico_lorello on 2016-02-24
Hi, thank you for the answer. I got this

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)
04:03.0 FireWire (IEEE 1394): LSI Corporation FW322/323 [TrueFire] 1394a Controller (rev 61)


that is the list of my actual driver I have already installed?
thank you

---

### Post by Jaswinder_Singh on 2016-02-26
I'm running Ubuntu 14.04 LTS on Macbook 4,1 as well for the past month. Here's what I've found -
1. Your Broadcom Airport Extreme wi-fi card may give you trouble with some wi-fi networks. Follow instructions in this thread - [http://ubuntuforums.org/showthread.p...4#post13052784]("http://ubuntuforums.org/showthread.php?t=2230194&p=13052784#post13052784"). This worked for me beautifully.
2. Your core fan will probably be giving you a lot of trouble, staying up at 6000+ RPM. Here's a solution for that - [http://ubuntuforums.org/showthread.php?t=1754431](http://ubuntuforums.org/showthread.php?t=1754431). However, this is giving me an error - 

Error!/usr/src/applesmc-0.17.4.dkms.tar.gz does not exist.dpkg: errorprocessing package applesmc-dkms (--configure):
 subprocessinstalled post-installation script returned error exit status 2
Errors wereencountered while processing:
 applesmc-dkms

But, in spite of this error the package is working fine and I'm able to control my core fan after following the instructions in that thread.

3. Your battery might show as "full" at 94% charge. That's normal, Apple hardware is designed to protect battery health by not allowing full charge and discharge cycles.

There might be some other things perhaps. But I hope this helps in some way. 

P.S. - If you find a way to fix the applesmc-dkms error issue, please share.

---

### Post by pestilence000 on 2016-02-28
I'm also using 14.04 LTS, and Ubuntu 4,1. I had the fan under control, using macfantld. But once I had done a SMC reset, the changes are gone. Now, I can't get it to work. I realize that there was a applesmc.768 folder in /sys/devices/platform which is gone. The macfanctld cannot access the temperature, and hence doesnot load. 

@Jaswinder_Singh : Did you manage to fix the issue? let me know. Thanks.
[I]
I get the following issue when I followed the 11.04 fix.

DKMS: add completed.
Installing prebuilt kernel module binaries (if any)
Building module...


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
make KERNELRELEASE=3.19.0-51-generic -C /lib/modules/3.19.0-51-generic/build SUBDIRS=/var/lib/dkms/applesmc/0.17.4/build modules.....(bad exit status: 2)
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.19.0-51-generic (i686)
Consult /var/lib/dkms/applesmc/0.17.4/build/make.log for more information.
dpkg: error processing package applesmc-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 applesmc-dkms

[/I]
But I can install the precise deb file "applesmc-dkms_0.18.1-precise-mactel1_all.deb"

---

