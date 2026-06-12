---
title: "How TO: make Ubuntu 10.04 Bootable for PPC Mac"
date: 2010-06-02
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-06-02
Okay, I've downloaded the Ubuntu 10.04 .iso for PPC mac. What do I do to the iso file to make it bootable? Keep in mind, all the stuff that i am going to be doing, will be done on a mac. 

P.S.  Please keep instructions as easy to understand as possible

P.S. AGAIN  I downloaded the Ubuntu 10.04 (for ppc mac) .iso from " [http://cdimage.ubuntu.com/ports/daily-live/current/](http://cdimage.ubuntu.com/ports/daily-live/current/) "

Thanks,
Ben

---

### Post by rjcalifornia on 2010-06-02
what are the specs of your mac?

---

### Post by 828688 Ben on 2010-06-02
Processor: Dual 2 GHz PowerPc G5
Memory: 1.5 GB DDR SDRAM
Graphics Card: ATI Radeon 9600

---

### Post by linuxopjemac on 2010-06-03
Follow [this thread]("http://mac.linux.be/content/kubuntu-ibook-g3-0") and replace live-nosplash-powerpc by live-nosplash-powerpc64.

To burn an iso, look [here]("https://help.ubuntu.com/community/BurningIsoHowto").

Hope that helps.

X will be a total different problem. We will have to see if we can get that working. Don't expect it to run automatically after installation.

---

### Post by linuxopjemac on 2010-06-03
You can also look [here ]("http://wiki.debian.org/iMacG5")for other stuff after installation.

---

### Post by sha.goyjo on 2010-06-03
To perhaps clarify, the iso file is a an image file of a bootable disk, which, when you burn it using the tutorial mentioned above, will produce a bootable disk. When you boot using the parameters also mentioned above, this should result in a successful boot.

I hope that helps.

---

### Post by Trooper1420 on 2010-06-03
Download the .iso
 
Open Disk Utility
 
Drag the .iso to the left column of disk utility
 
Select the iso i Disk Utility
 
click 'burn' at top left of disk utility
 
insert blank CD in the burner drive and let it burn
 
the burned CD should be bootable, but do not select it as boot disc from the OS X startup disc option- boot it by holding 'c' when you power on the system.
 
I used this procedure last week to burn a Lucid Lynx CD using my G4 Mirror Door. Booted on the CD and am now running Ubuntu on the G4 Mac.
 
Good luck!

---

### Post by 828688 Ben on 2010-06-03
First of all, thanks for all the great replies!

Secondly, I am not installing Ubuntu on to mac the normal way, I am using a virtualization program called "Q" = ([http://www.kju-app.org/](http://www.kju-app.org/)). 

I attached a picture of what happens when i try to boot from the disc, on Q.

[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TAgJr1VJNbI/AAAAAAAAASE/mXKIJimeHes/s720/Picture%206.png[/IMG]

As you can see in the picture, everything stops at "ramdisk loaded at 02600000, size: 12287 Kbytes". 

Any suggestions???

Thanks a lot for all the great help,
Ben

Link to picture:    [http://lh5.ggpht.com/_FI33gwIVx5s/TAgJr1VJNbI/AAAAAAAAASE/mXKIJimeHes/s720/Picture%206.png](http://lh5.ggpht.com/_FI33gwIVx5s/TAgJr1VJNbI/AAAAAAAAASE/mXKIJimeHes/s720/Picture%206.png)

---

### Post by linuxopjemac on 2010-06-03
I tried the same as you did once and I had the same result. Can't help you with this one...

Why don't you make a dual boot system ? The best of both worlds..

---

### Post by 828688 Ben on 2010-06-03
The reason I don't dual boot is because, as far as I know (I may be wrong), when I set up the new hard drive partitions, I have to delete all my stuff on my current partition so I can make all new patitions. 

Am I wrong, can i dual boot with Ubuntu and mac, and keep my current mac os x tiger partition intact, and NOT have to delete it? If I can, how do i do this?

Thanks,
Ben

---

### Post by Trooper1420 on 2010-06-03
Partitioning inherently wipes out the drive, in my experience. I don't believe you can repartition a drive and retain the contents of any existing partitions. Certainly not with any basic tools... Super Duper or some other utility might be able to do that, though I'm not sure.
 
The other issue is whether a Mac-formatted drive will let you install anything other than a Mac OS on it. 
 
For me, I have a bunch of extra drives sitting about and the G4 Mirror Door has four drive bays, so I built the Ubuntu on one of the spare drives that had been written to zeros.  This way, I don't have to touch my Mac drive or repartition anything to check out Ubuntu.

---

### Post by 828688 Ben on 2010-06-03
Unfortunately, at the moment, using another hard drive is not an option for me.

---

### Post by 828688 Ben on 2010-06-03
Okay, Can someone help me setup a program called "Mac-On-Mac"?

Link to Wikipedia page about "Mac-On-Mac": [http://en.wikipedia.org/wiki/Mac-on-Mac](http://en.wikipedia.org/wiki/Mac-on-Mac)

P.S.  you can run linux on Mac-On-Mac

Thanks,
Ben

---

### Post by sha.goyjo on 2010-06-03
> **Trooper1420 said:**
> Partitioning inherently wipes out the drive, in my experience. I don't believe you can repartition a drive and retain the contents of any existing partitions. Certainly not with any basic tools... Super Duper or some other utility might be able to do that, though I'm not sure.
 
The other issue is whether a Mac-formatted drive will let you install anything other than a Mac OS on it. 
 
For me, I have a bunch of extra drives sitting about and the G4 Mirror Door has four drive bays, so I built the Ubuntu on one of the spare drives that had been written to zeros.  This way, I don't have to touch my Mac drive or repartition anything to check out Ubuntu.

Erm, the standard tools that many people use to dual boot (refit and boot camp) both allow you to resize existing partitions without deleting them. Granted, there is always a list of extreme data loss, but I've never had it happen.

Just saying, changing partirons without data loss is not impossible. It just takes a lot of time, and it's a little risky. If you had to delete everything, nobody would ever do it.

---

### Post by linuxopjemac on 2010-06-04
As far as I know, you can shrink OSX partitions with Disk Utility in newer versions of OSX on Intel Macs, say Leopard. I also read that people did it on a G4. I would make a complete backup first with Carbon Copy Cloner onto a firewire disk (not expensive nowadays for say 40 Gb). You can also shrink with gparted from the Ubuntu liveCD. But as I said, always make a backup.

[http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini](http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini)

---

### Post by guidop on 2010-06-05
Although the Q Guest PC editing tool gives several choices, I've only had success running Q as an x86 processor emulator.  Since it's a software emulator, it runs very slowly compared with native the ppc host speeds.

As a test on my 1.8 GHz G5 iMac, Q Version 0.9.1d118:

I downloaded the Puppy Linux 5.01 .iso (x86 only).
(Puppy 5 is ubuntu lucid based.)

Configured Q (Hardware):
- Use the .iso image as the CD-ROM.
- Set Q to boot from CD-ROM
- Set no hard-disk
- Selected PCnet PCI network adapter.

Booted the virtual machine:
- Approximately 1/2 hour to get to desktop
- Approximately another 1/2 hour to use the first run tools to get the network up.
- Approximately another 1/2 hour to select the Puppy Browser as the default and browse to this web-page.

So it is possible to make an x86 linux variant "run" on Q, although "crawl" may be a better term.

Perhaps on your dual G5, it will run a bit faster.


I've also gotten Windows 2000 to run under Q, but it's barely usable, and it runs at about 1/2 the speed of Windows 2000 on Virtual PC 7 for mac (discontinued Microsoft PC emulator).


Edit:  Based on the Q Wiki, the Virtualizer portion of the Q project is currently ONLY for x86 virtualization on Intel Macs.

---

### Post by 828688 Ben on 2010-06-05
Yep, I have had about the same results as you. I just wish Q would work when not used as an emulator.

---

