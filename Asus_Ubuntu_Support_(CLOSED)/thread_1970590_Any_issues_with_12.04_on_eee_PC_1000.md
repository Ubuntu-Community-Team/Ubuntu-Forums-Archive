---
title: "Any issues with 12.04 on eee PC 1000?"
date: 2012-05-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Auslegung on 2012-05-01
[SIZE="3"][FONT="System"]Specifically the 1000HA.  I'm dual-booting Win7 and 10.04 currently, everything works well and I'm happy.  I've tried the LiveCD for an hour or so and things went smoothly, but I want to know from people who've had this as their daily OS for longer.  I did some googling of "12.04 eee pc 1000 issues" and nothing really comes up, but the 1000 line is old so that probably has as much to do with it as anything.  Whatever you can say will be a help.  Thanks[/FONT][/SIZE]

---

### Post by JRV on 2012-05-01
It runs okay on my EeePC 901, which uses the same processor and chipset.

---

### Post by djlemmings on 2012-05-01
> **JRV said:**
> It runs okay on my EeePC 901, which uses the same processor and chipset.
I just installed it on my 901 too but the LAN ethernet isn't working. Everyting else is fine otherwise.

How have you made the LAN to work?

Thanks.

---

### Post by wojox on 2012-05-01
> **djlemmings said:**
> I just installed it on my 901 too but the LAN ethernet isn't working. Everyting else is fine otherwise.

How have you made the LAN to work?

Thanks.

Did you turn it back on in BIOS. It shuts off when you install any OS on mine. :confused: Have to go back in and and turn it back on.

---

### Post by djlemmings on 2012-05-01
> **wojox said:**
> Did you turn it back on in BIOS. It shuts off when you install any OS on mine. :confused: Have to go back in and and turn it back on.
LAN is activated in th BIOS... I really don't understand...

---

### Post by JRV on 2012-05-01
On my 901 both wired and wireless worked out of the box.  
I do have an updated BIOS, maybe that is the reason.

---

### Post by djlemmings on 2012-05-02
> **JRV said:**
> On my 901 both wired and wireless worked out of the box.  
I do have an updated BIOS, maybe that is the reason.

I have the latest BIOS too, I don't really understand. The LAN was working perfectly on me Meego installation, but I wanted to try a more "up to date" OS...

Have you done a clean install (from scratch) or just an upgrade? It could explain a bit.

---

### Post by JRV on 2012-05-02
> **djlemmings said:**
> I have the latest BIOS too, I don't really understand. The LAN was working perfectly on me Meego installation, but I wanted to try a more "up to date" OS...

Have you done a clean install (from scratch) or just an upgrade? It could explain a bit.

It was a clean install.

---

### Post by djlemmings on 2012-05-02
> **JRV said:**
> It was a clean install.

Well, I really don't understand. I tryed to boot the live CD again to see if it was enabled by default, and still no LAN connection.

I'll try to find what's wrong...

ps : My Eeepc 901 was the XP release, the first one with 4 GB + 8 GB SSD drives.

---

### Post by JRV on 2012-05-02
> **djlemmings said:**
> My Eeepc 901 was the XP release, the first one with 4 GB + 8 GB SSD drives.

My Eeepc 901 was the Linux release, the first one with 4 GB + 16 GB SSD drives.
Is it possible we have different LAN hardware?

---

### Post by djlemmings on 2012-05-02
> **JRV said:**
> My Eeepc 901 was the Linux release, the first one with 4 GB + 16 GB SSD drives.
Is it possible we have different LAN hardware?
I don't know. Let see :) Here is the return of the command "lspci":

```

00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (r
ev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics C
ontroller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe
04:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev 
b0)


```

What is yours?

---

### Post by djlemmings on 2012-05-02
Ok, I desactivated the Wifi network in the Ubuntu menu and now the LAN is working... Can't understand... Anyway, things are fine now.

---

### Post by JRV on 2012-05-02
> **djlemmings said:**
> 

What is yours?

Mine are the same.

---

### Post by JoeRacette on 2012-05-08
I upgraded my 1000HA from 11.04 to 12.04 -all seems OK but the wireless won't connect.  Used to work fine.
Lot's of people with the same problem - check the networking forum.

---

### Post by bawig1 on 2012-05-10
Hi,

I have a Asus EeePC 1000P. I made a bootable USB stick with my Ubuntu laptop and booted it on the netbook. When I click on Try Ubuntu  and the desktop loads the wireless seems to work but when I try and connect to an access point the kernel crashes. When I tried to install it on the netbook the install when ok but when I booted I got a  kernel panic. I don't know what to do so I am going back to Netbook remix unless I can find a way to post these problems to the forums.

Brett.

---

### Post by Grant T B on 2012-05-14
I'm using a 901 and have some basic questions/issues. I installed 12.04 on the 4GB drive, selecting the option to erase it before doing so. Immediately after the installation I saw that Update Manager had over 100 updates pending. I attempted to install these, but was told that I had less than 100 MB remaining. Does the OS occupy all the other space?

It seems that the best solution is to install 12.04 on the 16GB drive. Is this true?

If I do this, what is the best way to erase the 4GB drive afterwards?

---

### Post by Auslegung on 2012-05-15
> **Grant T B said:**
> Does the OS occupy all the other space?

I guess it does.  My 12GB partition for / has 12.04 on it and nothing else, and it takes about 4.5GB of space.  

> **Grant T B said:**
> It seems that the best solution is to install 12.04 on the 16GB drive. Is this true?

You're probably right, it may be your only option.

> **Grant T B said:**
> If I do this, what is the best way to erase the 4GB drive afterwards?

It'll depend on what you want to do with it later.  If you want it just for hard drive space, format it using gparted (boot into a 12.04 LiveCD, install 12.04 on the 12GB partition, then use gparted to format the 4GB partition).  If you want it to be your /Home folder, I believe you can select that option while installing and it'll format it for you.

---

### Post by Grant T B on 2012-05-15
Since my last comment, I've done the following:

1. Attempted to install to the 16gb drive:  "Installation has crashed." 2. Formatted the 16gb drive with Disk  Utility. Tried to do the same for the 4gb drive, but "drive is busy." 3.  Attempted twice more to install to the 16gb drive. The first time I  took the option to "reinstall," and the next time this was not  available, so I chose "erase and install." There was no message about a  crash after either attempt, but neither was successful. There was the  same message each time, re: not being able to install all requested components.

Currently I cannot boot to either drive;  attempts to do this for either drive result in a black screen with white  blinking cursor in the top left, and the system unresponsive.

---

### Post by Auslegung on 2012-05-16
> **Grant T B said:**
> Tried to do the same for the 4gb drive, but "drive is busy." 

Maybe a dumb question, but did you do all this in a LiveCD?  If you're trying to do it by booting into the 4GB drive, you won't be able to unmount the 4GB drive to do the necessary formatting, installing, etc.  

As for the black screen, I've read a couple of people having that problem, googling might help you come up with some solutions.  Is it possible you had a corrupt download or something wrong along those lines?  Do an MD5 checksum thing [https://help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes").

---

### Post by Grant T B on 2012-05-16
Thanks for the response. I was trying to format the 4gb drive after having booted it. I understand now why that didn't work. 

Since my last post, I've lost the ability to boot from the usb drive, though I can view its files in Windows. A search did not find an .iso file on which to do a md5 check. Should I assume that I need a utility to do this? It seems that a utility that could create a bootable USB drive might  also be able to do md5 checksums. What is a good utility for either or both that will run on Windows?

---

### Post by Auslegung on 2012-05-17
Just googling windows iso to usb I came up with this: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

and googling md5 checksum windows I got this:
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by xdarkxanarchyx on 2012-05-26
Anyone able to confirm everything working perfectly "out of the box" with the regular 1000? I've got the Linux one with 8+32GB SSD's if it means anything.
Haven't had any issues with 10.04. I'd prefer to just to an CLI upgrade because my external optical drive is finicky and have never had much luck with USB boots (they always say they were made successfully but nothing happens when I try to boot from them but that's a topic for another thread and not a big deal).

---

### Post by Auslegung on 2012-05-26
Everything worked fine for me, though the update left out a few of my programs such as calibre, etc.  wifi is working, graphics, screen resolution, etc.

---

### Post by Grant T B on 2012-05-26
> **xdarkxanarchyx said:**
> USB boots (they always say they were made successfully but nothing happens when I try to boot from them 

This has consistently been my problem. It also occurred with EasyPeasy, though Mint installed without incident and was useable.

---

