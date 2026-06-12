---
title: "Cannot install linux on a Hyundai p571 laptop"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by sad_iq on 2007-10-27
Ok...here I am trying to install kubuntu on a laptop...everithing fails...booting from a live cd doesn't  work,only booted once, crashes since then. The crashes occure randomly, sometimes before the desktop loads, sometimes after and the system halts, so I cannot diagnosticate the problem. I have tried many live cd's (ubuntu,kubuntu sabayon..etc) , they all pass trough the same process. Installing from the alternate cd fails in installing grub..so I installed it without grub(my mistake), and now I cannot boot it. I tried booting with noacpi, nolapic same result. Also any live cd I put in boots fully only the first time, fails afterwards. It's a P4 2400, 254 MB RAM, some SiS video card...and don't know what else :(
 It gave me several times a kernel panic (but not always...using the same disk)...something about squashfs.
 So...any ideas??
edit: Forgot to say installing Windows also fails with some strange hardware errors!!!

---

### Post by Threbus5 on 2007-10-27
Hi,
Do you notice whether booting/running from a pen drive or floppy works?
Try running from a floppy version of DSL. Then check devices.
Could be a problem with the CD or DVD drive. 

Good luck.

---

### Post by sad_iq on 2007-10-27
I have not yet tried to boot from a pen drive yet, the cd has to be ok...it worked on 2 of my systems...and I do have many LiveCd's here, one has to be ok. Also memtest shows no errors. I will try to see if puppy linux works!!!
 Any more ideas??

---

### Post by dptxp on 2007-10-27
> **sad_iq said:**
> Ok...here I am trying to install kubuntu on a laptop...everithing fails...booting from a live cd doesn't  work,only booted once, crashes since then. The crashes occure randomly, sometimes before the desktop loads, sometimes after and the system halts, so I cannot diagnosticate the problem. I have tried many live cd's (ubuntu,kubuntu sabayon..etc) , they all pass trough the same process. Installing from the alternate cd fails in installing grub..so I installed it without grub(my mistake), and now I cannot boot it. I tried booting with noacpi, nolapic same result. Also any live cd I put in boots fully only the first time, fails afterwards. It's a P4 2400, 254 MB RAM, some SiS video card...and don't know what else :(
 It gave me several times a kernel panic (but not always...using the same disk)...something about squashfs.
 So...any ideas??
edit: Forgot to say installing Windows also fails with some strange hardware errors!!!

You have only 256 MB RAM, that is the problem. Make a SWAP partition of 512 MB or more with GPARTED first. Ubuntu/Kubuntu Live CDs shall not rubn otherwise.

---

### Post by sad_iq on 2007-10-27
Like I said...I already installed ubuntu from the alternate cd but installation failed to install grub...so the swap partition was created. I booted puppy linux...it runs ok...until I open 2 apps at the same time(like console and web browser)...then it halts. I could not see any errors from dmesg...or at least none that struck me in the eyes. I don't know what else to do from here :( Also googleing for an bios update is a really long shot...and installing any such update without an os is a pain :(
 So far I am standing with a nice looking worthless bunch of hardware someone might call a laptop...so Please Help with more ideas!!!

---

### Post by gn2 on 2007-10-27
Have you tried a different hard drive, or tried deleting all the partitions and starting from scratch with the Alternate CD?

With 256mb RAM, Xubuntu 7.04 would perhaps be a better choice?

---

### Post by sad_iq on 2007-10-27
Unfortunately I don't have a spare hdd for a laptop...so I cannot try that. Every time I try to install I do a complete rewrite of the partitions of the hdd. I've been thinking about xubuntu, but before I erased the hdd I had windows xp working pretty fine...no lags...nothing...so I assumed that ubuntu would work ok.
 Also running puppy linux stops if i open 2 apps at the same time like I mentioned earlyer, so I asume the same would happen with xubuntu

---

### Post by dptxp on 2007-10-27
Try PCLINUXOS 2007. You can also try Knoppix, but Knoppix is hard to install. Damn Small Linux is another option, their version 4.0 has been recently released.

Post you problem with Puppy on Puppy forums or try their previous release.

Check your video RAM in bios, the shared video memory should be 64 MB.

---

### Post by sad_iq on 2007-10-27
The shared video memory is set to 64 Mb, so is Agp Aperture(or what it's called). The idea about posting in puppy forums isn't that bad, but I would also have to post it in Ubuntu, kubuntu, gentoo, sabayon, arch(tried to install it), and lately mandriva(the most succesfull one so far). Thank GOD I have no download limit from my ISP and it only takes less than half hour to download a full .iso...right now downloading Open Suse, it's actually a great way to renew my LiveCd collection and see the diferent themes and styles used :)
 Now back to the point ...I suspect a serious overheating problem, so I will have to take a nice screwdriver and take the laptop to pieces to clean the dust out and see how it goes afterwards!!!

---

### Post by gn2 on 2007-10-27
If you have 256mb RAM and 64 of that allocated to graphics, the Ubuntu Live CD should not run as there isn't enough RAM.

Try installing from the Xubuntu 7.04 Alternate CD would be my advice.

The Alternate CD usually works better in my (limited) experience.

It's actually very simple to use the 7.04 Alternate CD.
Boot the CD, then select the "Install a command-line system" option.
The installation process is roughly the same as the installer in the Live CD.

Eject the CD, re-boot, log-in, insert the CD and enter "sudo aptitude install xubuntu-desktop"
(substitute ubuntu-desktop if using the Ubuntu Alternate CD)

Re-boot and you'll (hopefully) have a working system.
__________________

---

### Post by sad_iq on 2007-10-27
That's what I've allready tried...but instalation failed in installing grub...so I skiped that step :( (big mistake). Also all the LiveCd's I've tried DO boot up ok, but they hang after about 10 minutes(puppy also hangs) or when opening too many apps at the same time, then booting the same disk the second time is impossible(that's why I suspect overheating). The only succesfull boot I've had is a Mandriva disk, retrying the second install right now...hopefully it won't crash(again). And how is it possible to have a perfectly working Windows Xp instalation on this laptop(had one before I formatted) and not have a gnome or kde desktop?? Also...can the Hdd have phisical damage in the MBR?? Can I check it??? Can I mark these blocks as bad blocks or something(there was something in windows that could do it)???

---

### Post by sad_iq on 2007-10-27
Booting again from the alternate cd...same as all other cd's only worked the first time...second time is a no go :( Anyone have any more ideas???

---

### Post by dptxp on 2007-10-27
Xp runs on 128 MB RAM and no computer can sell (exclude Apple etc) if Windows does not run on it. So it is not surprising that Xp runs well on your laptop.

I run Ubuntu on desktop with 256 MB RAM out of which 64 MB goes to video memory, obviously I had to
make a SWAP partition first. Since you too have a SWAP (of at least 512 MB), RAM is not your problem.

Carry out a memory check with your Ubuntu Live CD, it is there just after the boot.

---

### Post by sad_iq on 2007-10-28
I have done a memory check with 2 diferent LiveCD's I tried(ubuntu and mandriva), right now I'm playing with Ultimate Boot Cd: [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/) It has some (plenty) good tools to check the hardware, so far...things are ok.

---

