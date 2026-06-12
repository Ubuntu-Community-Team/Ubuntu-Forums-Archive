---
title: "new ubuntu install"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by g.hughes on 2007-04-15
Hi, all.
I am running WindowsXP home on C drive. A second internal HDD has benn partitioned into three NTFS drives of 60GB, 60GB and 40GB using Windows partitioner, leaving 30GB unused space.
I have ubuntu 6.10 DVD from January 2007 Linux magazine. My aim is to dual boot the system in Windows and ubuntu; with ubuntu installed in the 30GB free space on the second HDD.
Is it OK to load the DVD and follow the instructions or is there something I am unaware of?
Needless to say I am new to this.

---

### Post by BaffledMollusc on 2007-04-15
I've never used the DVD install, only the CD install, but I presume the DVD will be the same, except with more software on it.

If this is the case, yes, all you have to do is put the DVD in and boot from it (if the DVD drive isn't the first boot device you may need to change the boot order in the BIOS).

Ubuntu should then boot up in live-CD mode, so you can try it out without making any changes to your hard drive. To install, click on the "install" icon on the desktop and follow the prompts. When it comes to the partitioning stage, all the partitions should be visible and you can choose the free partition to install on. The install will automatically install a boot menu, so that on boot you can choose between Windows and Ubuntu.

---

### Post by Bartender on 2007-04-15
g. -
You have a blank HDD, right?  Nothing on it?

Tell you what I'd do.  I'd unplug the drive with Windows.  Unplug the data cable entirely.  I'd unplug the power too but that's just me.  Your Windows drive is now safe from any mistakes you might make during Ubuntu installation.

Then I'd experiment with Ubuntu for a week or two, and take notes!

Try letting Ubuntu auto-install to the first of those partitions on the second drive.  Try manually re-installing to the same partition.  Try installing to the whole drive.  Try dual-booting Ubuntu on the same drive.  You'll learn a lot about GRUB if you try some dual-boot experiments.  You want to get comfortable with the way Linux names partitions, and you'll want to gain some insight into how GRUB works.  GRUB is the Linux bootloader that Ubuntu uses.

Check out your PC's bootup options.  Lots of PC's are set up so that as they're booting you tap on one of the keys and you'll get a screen asking which device you want to boot.  If your PC has that option, the absolute safest way to dual-boot is to have one drive all-Windows, and another drive all-Linux, and choose which one to boot at startup.

Once you gain some insight into how it all fits together you might feel you're ready to try dual-booting.  Read some of the many many threads and websites on dual-booting, save all your personal data to CD's or whatever, and set up a real dual-boot so that you don't have to tap on keys during startup.

Don't worry about the partitions you already made - it's easy to make them again with a GParted LiveCD.  I'd suggest you download the .iso and make a bootable GParted CD anyway.  Nice tool to have around the house.

---

### Post by Maestro23 on 2007-04-15
Good post from the person above. You will want to install Ubuntu in that free space.  Manual Partiton is the option you want to do. During the install, you will need to create 3 partitons:

> / = root

/home (Your personal files go like pics, mp3, etc...)

swap

*Make the / and /home partitions pretty big.

Just my 2 cents.:D

---

### Post by vanadium on 2007-04-15
You just are wanting to try Ubuntu and have a free spare partition. This is a perfect scenario. I wouldn bother too much on the technical side for now. Just use  the default install of Ubuntu and have it use your emptypartition (which it'll probably suggest as a default). It is a very user-friendly install. Ubuntu will setup a bootmanager. When you boot your system, you will be able to choose booting into Windows or into Ubuntu.

I installed Ubuntu one week ago. I took one step further and just clear wiped Windows XP from my laptop (a Dell D810 Latitude). It just went on perfectly. My wireless network suddenly has become rock solid stable  (it must have been Windows then! Not my router!).

Doing the full transition is a matter of getting used to the new operating system and its software. For me, the software isn't the issue, because it just stayed the same. The only caveat is that you'll have to look very carefully when you buy devices, make sure that they are supported under GNU/Linux.

---

