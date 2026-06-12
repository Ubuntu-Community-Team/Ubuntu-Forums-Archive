---
title: "new to linux...can't get anything to work"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by sjewenp on 2006-12-15
i am a lifelong windows user who is trying to branch off but having severe difficulty.
i am trying to set up a dual boot on two drives.  one drive is an ide drive (my ubuntu drive) and the other is two drives in a raid0 configuration. (my xp drive) the only way i can boot to ubuntu is if i change the boot order in my bios.
i am also having major difficulty in internet connection.  ubuntu sees that i have a wireless card, but when i try to enable it (including ssid and wep) i get nothing.  no error message or anything.  i have read the wireless tutorial and am getting nowhere.  please help!

---

### Post by aysiu on 2006-12-15
I don't know the difference between IDE and RAID, but I know what details you can give that might be helpful to those seeking to help you:

1. Did you install Grub to the MBR (Master Boot Record)?
2. What brand is your wireless card?

---

### Post by patrick.dylan on 2006-12-15
> **sjewenp said:**
> i am a lifelong windows user who is trying to branch off but having severe difficulty.
i am trying to set up a dual boot on two drives.  one drive is an ide drive (my ubuntu drive) and the other is two drives in a raid0 configuration. (my xp drive) the only way i can boot to ubuntu is if i change the boot order in my bios.
i am also having major difficulty in internet connection.  ubuntu sees that i have a wireless card, but when i try to enable it (including ssid and wep) i get nothing.  no error message or anything.  i have read the wireless tutorial and am getting nowhere.  please help!

Don't give up! There's lots of friendly help available on these forums, and the more detail you provide, the more help you'll receive. 

For booting, you could try having the system default to one OS and use a boot disk for the other.

Have you tried the ndiswrapper method for your wireless card? [See the guide]("http://ubuntuguide.org/wiki/Main_Page") for instructions.

---

### Post by sjewenp on 2006-12-15
my ubuntu is on an ide drive and i have windows installed to my raid drive which is sata.
my wireless card is linksys.
i don't know anything about grub (totally new to this) i just followed the install wizard.
if ubuntu didn't recognize my card, would it showup as an option under network connections?  (it does by the way)

---

### Post by aysiu on 2006-12-16
There are a bunch of Linksys models.

This page may help you out a bit:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by sjewenp on 2006-12-16
ok...i have to type this out longhand, as i can't cut and paste.

Broadcom corporation BCM4318 [AirForce One 54g]
802.11 Wireless LAN Controller (rev 02)
Subsystem: Linksys: unknown device 0042
Flags: bus master, fast devsel, latency 64, irq 90
memory at feafc000 (32-bit, non-prefetchable) [size=8k]

---

### Post by sjewenp on 2006-12-16
ok, i just dragged my huge computer across the room and connected it to the internet.  the drivers are available for my wireless card but they're in *.exe.  how do i use this?

---

### Post by 3rdalbum on 2006-12-16
Download "ndiswrapper" and "ndisgtk" from the repositories - either by connecting your computer to wired broadband and using Synaptic, or by using another PC to download these files from [http://packages.ubuntu.com](http://packages.ubuntu.com).

If the latter, then you must install ndiswrapper first, then ndisgtk.

When they are installed, the new program will be under System > Administration.

Is there a .inf file that comes with the Windows application? If so, then just transfer that to your Ubuntu machine, open up the new administration program, and tell it where to find the .inf file. If not, you may need to install the drivers onto a Windows machine and find the .inf file that it installs.

---

### Post by sjewenp on 2006-12-16
ok, got the files and installed the driver...it's saying my hardware isn't present

---

### Post by Simanek on 2006-12-16
> **sjewenp said:**
> i am trying to set up a dual boot on two drives.  one drive is an ide drive (my ubuntu drive) and the other is two drives in a raid0 configuration. (my xp drive) the only way i can boot to ubuntu is if i change the boot order in my bios.

If you change your BIOS to boot the IDE drive first, Ubuntu boots. Right? In that case, as the machine is booting you should first see some information about your computer in text (BIOS type, processor, maybe the manufacturer) after that you should see some text referring to GRUB and then for a short time see an option to press a key to see more options. GRUB can be used to select different Linux Kernels to boot from as well as different operating systems. Did you get asked any questions regarding alternate operating systems during the Ubuntu installation process? With a dual-boot system on one HD it seems to me that the installer sets it up for you. I can't tell you how to configure GRUB to point to your Windows raid0 drive at the moment, but I wanted to help you understand what GRUB does. It's as simple as editing the GRUB configuration text file.

---

### Post by sjewenp on 2006-12-16
it boots but when i hit escape, ubuntu won't see my windows os.  if i change the boot order then windows won't see ubuntu...

---

