---
title: "MAC Ibook 500 MHZ dual boot UBUNTU 7.04 and MAC OS9"
date: 2007-07-07
forum: Apple PPC Users
---

### Post by captcadwallader on 2007-07-07
I have tried to dual boot my IBOOK, 500 mhz, 640 megs, 100 gig notebook.  I was able to install 7.04 with the alternative install CD and modifying the screen resolution.  Thanks to the forun for the instructions on how to do that.  However,  When I install OS 9 first, create two partitions and intall OS9 the OS 9 works fine.  Then when I try to install Ubuntu I can get Ubuntu to install OK but I lose OS9.  From what I can tell UBUNTU overwrites the boot sector of OS 9.  Probably the wrong terminology, but this is what it seems to me.  When I boot holding the option key I see a os9 icon and a linux icon.  When I hit the OS9 icon, i get a MAC icon with a question mark in the middle of the icon that flashes forever.

Does it matter if OS 9 is the first partition or last?

If I can't boot to OS 9, but I install Mac on Linux, will MOL allow me to use OS9?

Any thoughts on how I would do this.  

I have OSX on my MacBook so I am using the IBook as the expermintal pc. 

I admit that there is only a limited reason for trying to dual boot both OS 9 and Ubuntu, but I thought I would try it.

Any thoughts would be appreciated.

---

### Post by 3rdalbum on 2007-07-08
Try booting up the Mac OS 9 CD, and selecting the OS 9 hard disk in the Startup Disks control panel. This should make OS 9 bootable again.

Unfortunately, this will cause you to lose easy access to Ubuntu. No worry though. Reboot and hold down the Command-Option-O-F keys, this will bring you to the Open Firmware prompt.

At this prompt, type:

```
boot hd:1,yaboot
```

If this doesn't bring you to the Yaboot bootloader screen, then increase the number until it works.

Now, you can either keep the situation the way it is - where you have to go into Open Firmware and type that command whenever you want Ubuntu - or you can try reinstalling Yaboot. In Ubuntu, go to the terminal and type:

```
sudo ybin
```

This will reinstall Yaboot, hopefully not stopping OS 9 from starting up again.

If your OS 9 partition does not mount when you've got the OS 9 CD booted up, then it looks like something has gone wrong and you'll have to reformat.

---

### Post by guidop on 2007-07-21
I have experienced the same issue when trying to perform a clean Feisty install on a triple booting (Ubuntu OS9 OSX) slot loading iMac.  Some additional searching shows the same issue occurring with installs of the latest Debian Etch:

[http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg58334.html](http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg58334.html)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422836](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=422836)

I think the problem lies with an updated partitioning tool used by the Feisty and Etch installers, but don't yet have proof.  At this point I don't even know which partitioning tool and version the installers use.  I've spent the last week looking for a work-around, and hope this doesn't come too late to help you.  As far as I know, there's no way to recover OS 9 booting without re-initializing and re-formatting the hard drive.

I DID finally manage to get Feisty (7.04) installed while maintaining OS 9 booting capability.
My path was a bit more convoluted, but first I'll cover the general steps I THINK should work for you:

1) Burn an Ubuntu Dapper (6.06) install CD.  (Edgy will probably work, too.)

2) IF you have backup utilities and external disk storage, save what you need from your OS 9 and Feisty installs (such as xorg.conf).  Note that any Mac OS 9 based utilities probably won't even see your disk.

3) Boot a Mac OS 9 install CD, use Drive Setup to initialize your hard drive, making 2 partitions, or 3 if you want an HFS share partition.    

4) Install OS 9 on one partition, and verify it works.

5) Boot from the Dapper install CD, choose the server option, and select manual partitioning. Delete the partition you want to install Ubuntu on, and make an 820 KB* boot partition at the beginning of the freed space, and the format remainder of free space as ext2 or ext3.  Write changes to the disk, then abort the install.  
Note that the boot partition is supposed to be 800 KB, but the Dapper installer wouldn't let me continue if I made it less than 820 KB.

6) Boot from the Dapper install CD again, execute a shell.  Run mac-fdisk to re-order the boot partition as partition # 2.  Exit the shell and manually power off when the system hangs.
You might be able to do this without rebooting, by executing a shell in a different virtual terminal, and running mac-fdisk that way.  I don't really know that it's necessary, although the mac-fdisk tutorial says the boot partition should be the second entry in the partition table.

7) Boot from the Dapper install CD, choose the server option, and select manual partioning.  Delete the Linux partitions you made, and make the boot, root, and other partitions you will use.  Remake the boot partition first, it should be # 2 in the partition table.  Remember the number of the partition you installed OS 9 in.  Abort the install.

8) Boot from the Feisty install CD, choose expert mode, DON'T use the partitioner, install in the partitions made with the Dapper CD.

9) Boot into Feisty, modify /etc/yaboot.conf to add macos=/dev/hdaX, where X is the OS 9 partition.

10) Reboot, and verify you can boot OS 9.



I took a longer path, but I KNOW it worked for me:

0) Install Ubuntu Feisty, using the partitioning tool.  Find out I can't boot OS 9.  OS X still works fine, and can see the OS 9 partition, but even using OS 9 utilities on CDrom, won't see any partitions. 

1) Have OS X, OS 9, and Dapper install DVD and CD's.

2) Back up necessary OS 9, OS X, and Feisty install files.

2) Boot from OS 9, make 4 partitions, with the one intended as a shared partition formatted as "Mac OS Standard (aka HFS)," others as "Mac OS Extended (aka HFS+).

3) Install OS 9.

4) Install OS X.

5) Boot from Dapper CD, choose server install, partition manually, complete server install.

6) Boot into Dapper on hard drive, run mac-fdisk to re-order boot partition as # 2, discover ybin doesn't work, mkofboot doesn't work, complains boot partition too small.

6) Boot from Dapper CD, choose server install, manual partitioning, delete and re-make 820 Kb boot and other Linux partitions.  Boot partition remains # 2 in table.  Complete Dapper installation.

7) Boot into Dapper on hard drive and log in.  Modify /etc/yaboot.conf to add OS 9. Reboot several times to verify triple boot works.

8) Boot into Dapper and log in.  Modify /etc/apt/sources.list for Feisty upgrade.  For a very useful sources.list generating tool, see:

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Run: 
  $ sudo apt-get update    # Verify no errors.
  $ sudo apt-get dist-upgrade   # Answer some config questions.
  $ sudo apt-get -f install     # Checked upgrade, and noted that there are no additional packages.
  $ sudo dpkg --configure -a    # Nothing done/needed.

  $ sudo reboot

9) Boot into Feisty.  Reboot several times to verify triple boot still works.

10) Boot into Feisty and log in.  Run: sudo apt-get install xubuntu-desktop  # Answer a few config questions.

11) Run: startx  See xubuntu splash screen, but discover X won't start.  Check logs, modify /etc/X11/xorg.conf to better match original clean Ubuntu Feisty install, get X working.  Start configuring XFCE desktop.  Use GUI upgrade tool, note that Feisty ppc now installs upstart, but don't notice faster booting.  (Really did notice a big improvement in boot time on a MacBook Pro upgrade from Edgy to Feisty.)  Still more to be done.

12) Write this up and call it a night.  Steps 1 to 12 took me 2 nights and a full day on a 400 MHz G3 slot-loading iMac, after a week of false starts.


I hope this helps someone else.  Would like to hear feedback, and whether my proposed method works.
I apologize for the lack of formatting, this is just a copy of my text notes.

- G Paolini

---

### Post by fkdev on 2007-07-22
Have you tried re-installing the mac os 9 disk drivers from the mac os 9 cd? You can do it from one of the disk utility apps on the cd.

---

