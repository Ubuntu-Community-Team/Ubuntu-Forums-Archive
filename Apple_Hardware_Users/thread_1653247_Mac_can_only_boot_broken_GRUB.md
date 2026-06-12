---
title: "Mac can only boot broken GRUB"
date: 2010-12-26
forum: Apple Hardware Users
---

### Post by biobunny on 2010-12-26
You read the title, when booting I can only acces a broken GRUB and this is how I might have done it wrong. I installed Ubuntu the first time using dual-booting which I think is the worst way since it could be done better by using a Virtual Machine such as Parralels or VMware. Well later I noticed that after removing Ubuntu there was still 2 problems 1.when selecting a OS during startup  When I select "Windows" it goes to a broken GRUB which displays something like this " Use tab to complete the first commands" GRUB><where you're suppose to type> and I can't type so I hard reboot it. 2. I could not get rid of LinuxSwap. Much later I removed LinuxSwap by booting in a Ubuntu live disk and then removing the partition as well as the Linux "/" and after booting to Mac OS X leopard disk0s1 the Mac OS X system partition was mounted which was bad since it was suppose to be invisible to even the root user unless viewed by terminal on any user. Now later I reformatted it as "Mac OS X something extended" and at first it was unjointed and impossible to mount and after I reformatted it it appeared as disk0s3. Now the problem appeared.
This is the stuff I can do
1. I can type some commands in the GRUB but when I typed find / the output is something like can't find /
2. I might be able to boot up a live disk however my Linux Ubuntu live disk is broken.
3. this is my dad's second hand Mac G5 iSight, not mine and it was a bargain, it was cheaper than my iPad with Mac OS X Leopard 10.5# 
4. I'm new to Ubuntu forums

---

### Post by guidop on 2010-12-28
Try booting while holding the 'option' key.  Open firmware should scan your drive for bootable partitions.  It will probably find two choices, one with an small penguin icon in the lower right, and one with a small OSX icon.  When the hourglass icon changes to an arrow, use the mouse to select the OSX partition, then the right arrow icon to boot.


If this lets you boot into OS X you can then try the following to make your system to default to OS X:

Log in to an account with administrator privileges.
(Typically the first account created has these privileges.

First, try opening the OS X "System Preferences" panel, selecting "Startup Disk," looking for and selecting your OS X startup volume.

Reboot and see if this now automatically boots into OS X.

If that was not successful, reboot with the option key and log in again. 

Open a terminal and type (and see) the following:

```
MyMac:~ UserName$ ls /Volumes
MacOSdiskPartition

MyMac:~ UserName$ sudo /user/sbin/bless --mount "/Volumes/MacOSdiskPartition" --setBoot --verbose
Password:
<A confirmation message that this worked.>

```

(Replace "MacOSdiskPartition" with the actual name of the OS X partition returned.)

Reboot and see if this worked.



As for removing the extra partitions and recovering disk space back to the original volume, I don't know of any free tool capable of expanding an HFS file system.  Last time I tried, gparted could only successfully shrink a non-journaled HFS partition. 

If you have an external FireWire hard drive, you could use a tool like Carbon Copy Cloner to make a bootable duplicate of your OS X partition, boot from it, then reformat the iMac hard drive as a single HFS partition, and restore from the backup.


The G5 is PowerPC (PPC) architecture:

Parallels, VMware, VirtualBox and other virtualization software are x86 architecture only.  As far a I know, there are no good virtual machine tools for the G5.

I think the default bootloader for PPC is still yaboot.
Are you seeing a screen somewhat like this?
```
First Stage GNU/Linux Bootstrap
Press l for GNU/Linux
      x for MacOSX

Stage 1 Boot: _
```

---

### Post by biobunny on 2010-12-28
My mac is a Intel version. I have the latest Mac g5 which is a Intel version. Also when I press option while booting it only displays "Windows" and that goes to the broken GRUB and I know I have not erased the Mac partition. also last time I booted into Mac OS X it thinks that the only OS on the Mac is Mac OS X Leopard

---

### Post by guidop on 2010-12-29
1) Can you identify the exact model of iMac using this site:  [http://www.everymac.com]("http://www.everymac.com") ?

2) Are you still able to boot into OS X using the option key method?  Did you try using system preferences to select the OS X partition as the startup disk?

3) Do you have an OS X (Leopard or Snow Leopard) install disk?

If this is an Intel mac, and you let the Ubuntu installer default to installing GRUB on the MBR instead of manually installing onto the Ubuntu partition, you may have to reinstall OS X to fix this.

If you can, boot the OS X install disk, and try the "_**archive** and install_" option to put a fresh OS X installation on the drive, and fix the GUID/MBR so OS X will boot normally.

With OS X reinstalled, disk utility or boot camp _may_ be able to grow the OS X partition back to the full disk.  If not possible from the boot drive, you may be able to do so by using the disk utility app available when booting from the OS X install disk. 

4) If you have important data on this machine, I would still try to find a way to make a backup first.  The best backup method will depend on what other computers and external hard drives you have available.

5) If you don't care about any applications or data on the hard drive, you could also just to a complete reformat to a single partition, and perform an erase and install of OS X.

---

### Post by biobunny on 2010-12-29
I've got a iMac core duo, the first Intel iMac. I cannot acces Mac OS X by the option key, not even by single-user mode. I also do not have a Mac OS X disk and today I'm going bring the mac in for fixing at a shop =(.

---

### Post by guidop on 2010-12-29
If you live in the US, the Mac Snow Leopart (OS 10.6) retails for $29, probably a lot less than your shop visit will cost.  Repartitioning and installation of OS X is pretty straightforward.

---

### Post by biobunny on 2010-12-30
I already brought it in, so too bad but thanks for your suggestions guidop.

---

### Post by biobunny on 2010-12-30
Actually the shop claims I erased Mac OS X but reformatting a partition does not erase Mac OS X right? Also I should have DIY because they fixing it cost $100 plus me having no idear if they save my full / directory or not.

---

### Post by biobunny on 2010-12-31
They erased my entire / directory =( and I had a lot of apps so remembering all of them one by one is pretty horrible.

---

### Post by guidop on 2010-12-31
It's possible that when you installed Ubuntu, a small mistake wound up damaging the partition tables or formatting or installing over the OS X partition.  Also the OS X Disk Utility, depending upon version and what you try to do, may wipe data, but I think it will warn you first.

I think the most common error, however, is to let the installer put GRUB at the MBR, rather than manually forcing it to install on the Ubuntu partition. 


If you get brave enough to try again, this post, and the referenced lifehacker post, is a good place to start:

[http://ubuntuforums.org/showthread.php?t=1564943]("http://ubuntuforums.org/showthread.php?t=1564943")

(Note that some of the linked model specific guides forget to tell you to install GRUB in the right place.)


Otherwise, Parallels, VMware or VirtualBox (free for personal use), should allow a normal single boot installation on a virtual disk.  3D affects may not work, however.  Sound support on the OS X hosted VirtualBox 3.x was not very good, either.  I haven't yet tested version 4.


[By the way, every new Mac should come with a software install disk.  Maybe your dad still has it.  It might help get back some of the missing applications.]

---

