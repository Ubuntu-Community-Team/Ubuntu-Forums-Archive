---
title: "help needed for repartitioning and multiboot setup"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by harmlesscat on 2007-10-19
I'd like to install Kubuntu.  I installed another variety of Linux a couple years ago, but I don't remember a lot of the details, so I consider myself very green when it comes to Linux disk partitioning, bootloading, and so forth.  (For what it's worth, my current Linux is Gentoo; I shouldn't have installed a 'developer' variety of Linux, but I took someone's advice at the time.)

Here's how I got my current setup:

I started with Windows XP, and installed Partition Magic and Boot Magic.  I repartitioned my HDD to make space for Linux and installed Boot Magic as the bootloader for the computer as a whole.

One of my Boot Magic boot entries is for Windows, the other says "Linux".  When I boot that, what actually boots is GRUB.

Within GRUB, I just have the one existing Linux kernel.  I believe I want to install Kubuntu to be booted from GRUB as another kernel.

Here are my current partitions, as seen from a couple of different commands.  One command shows the Windows stuff also and the other does not.

# fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               6        4113    32997478+  17  Hidden HPFS/NTFS
/dev/hda2            4114        7289    25511220    f  W95 Ext'd (LBA)
/dev/hda3               1           5       40131   16  Hidden FAT16
/dev/hda4   *        7290        7296       56227+  83  Linux
/dev/hda5            4114        4241     1028128+  82  Linux swap
/dev/hda6            4242        5516    10241406   83  Linux
/dev/hda7            5517        7289    14241591   83  Linux

Partition table entries are not in disk order
# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda6              9920032   4068448   5339516  44% /
/dev/hda4                54448     11108     40532  22% /boot
/dev/hda7             13796868   4389716   8837492  34% /home
none                    240824         0    240824   0% /dev/shm

I have downloaded the new 7.10 Gutsy Gibbon release of Kubuntu and burned it onto a CD, and it boots fine as a LiveCD.  But I'm kind of afraid to let it install itself from the CD.  I see from existing forum links that the install program can create new partitions, but since I have two levels of booting and partitions, I want to be as careful as possible not to wipe out anything I'm currently using.  Ideally, I want to install Kubuntu as a new choice under GRUB, and have the disks mounted so that it won't overwrite any of my current Gentoo Linux files.  I'm thinking that I may need a more manual process here.

What (I think) I want to do is, repartition hda6 and hda7 to split them in half (since both are less than 50% full), to allow for new partitions (hda8 and hda9 I suppose) for Kubuntu.  I know that fdisk can repartition disks in Linux, but I'm not sure of the exact command syntax to repartition in this manner.  

I'm also thinking that I will need to defrag hda6 and hda7 so that the repartitioning doesn't blow away any used space.  I don't know what command or tool I should use in Linux to defrag, or if it is even possible in Linux to defrag and repartition like this without corrupting existing files.  (Maybe I could do the repartition from Partition Magic in Windows, but I'm not sure how smart Partition Magic is about knowing what parts of my Linux partitions are used space.)

Once I have repartitioned, I'll need to install Kubuntu.  Maybe once I've done the repartitioning, I could use the Graphical Install - except that for consistency, I'd like Kubuntu to show up as a boot choice under GRUB, not under Boot Magic.

I want to be able to see my existing (Gentoo) Linux files, which I hope would be possible by mounting them differently when Kubuntu boots - e.g. mounting hda4 as /oldLinuxRoot and hda7 as /oldLinuxHome or something like that.  But I don't know how to make the devices mount differently when different kernels boot from GRUB.

(Once I get comfortable with my new Kubuntu installation and copy my data files over from my old Gentoo installation (hopefully within a couple weeks or so), I'll delete all those files, leaving space room to grow or to install something else in the future.)

Again, I have read that the Kubuntu Graphical installer allows manual editing of the partition file, but I'm not sure how smart it is for a setup like mine.  If the installer will handle my situation, great, but I'd like to hear that from an experienced person before I risk wiping out my existing files.  Otherwise, if someone can give me guidance on a more manual process, I'm willing to follow that.  

Any help will be appreciated!

---

### Post by mikeyphi on 2007-10-19
The GUI installer has a manual partition option - it gives you good control over what you want to do.
The Grub issue I'm not sure about - the installer will want to install Grub and overwrite the MBR. Not sure if the alternate CD would give you control over the Grub installer.

---

### Post by Daveth on 2007-10-19
my, that looks a complicated set-up, so do be very careful. You would do better running Gparted to partition those parts where Ubuntu might live. I suggest having a read of 

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

then load up a live cd, and re-partition from that. Remember to defrag any windows partitions that will be resized. I'm pretty sure that ubuntu would find both Gentoo and certainly any windows os- just seems rather too wobbly a setup to throw Boot Magic into the game as well. Just a thought:)

---

### Post by harmlesscat on 2007-10-22
Thanks for the suggestions so far.  After reading the replies, I was going to use gparted to repartition, but it said the partitions were in use and needed to be unmounted.  Apparently I needed to create a LiveCD just to boot gparted in order to do the repartitioning.  I had done some other reading in the meantime, and I decided I could safely repartition my Linux partitions with Partition Magic while running under Windows (so the Linux partitions wouldn't be in use at the time).

Thus, I have resized my Linux ext3 partitions, and my existing Gentoo installation still works.  I now have plenty of free space to install Kubuntu.

Which brings me to the boot loader issue.  As "Daveth" noted, I have a somewhat complicated setup with a chain of loaders.  But apparently what I am doing is not unheard of.  For example, I found this thread which is endeavoring to do a setup similar to mine:

[http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html](http://www.techspot.com/vb/all/windows/t-37980-dual-booting-linux-with-bootmagic-instead-of-grubHelp.html)

My main question about this other thread is, regarding the comment "When you installed Linux, you were asked whether to install GRUB to the MBR of the hard disk or to the Linux partition. You should have chosen the second option." -

In my case, GRUB is already installed, and it is not installed into the MBR.  Will the Kubuntu installer be smart enough to find the existing GRUB installation and insert itself as an entry there instead of trying to insert itself as an entry in Boot Magic (which apparently has issues booting Linux directly)?  I.e., I want to boot Kubuntu from GRUB, not from Boot Magic (which is what is in the MBR).  If the Kubuntu installer may have trouble with this, is there any way for me to do this manually?

One other thing to note -

The reason I have the chained bootloaders is that at one time I read or was told that Boot Magic would not directly boot Linux (hence it needs to boot GRUB which will boot Linux), and I was also told that GRUB would not directly boot Windows XP.  I have since read that there are other bootloaders out there which may be better than both Boot Magic and GRUB, but since I have a setup that works, as the saying goes, "if it ain't broke, don't fix it."  

If in fact Boot Magic will boot Linux, then perhaps I can let the Kubuntu installer insert itself as an entry in Boot Magic after all instead of needing to have it inserted under GRUB.  I'd just like to hear from an experienced user who can suggest which is the easiest and more likely way to get it to succeed.  I'm being cautious by asking before trying something to try to avoid going through a complex process to recover a failed installation.

---

### Post by harmlesscat on 2007-10-25
I believe I have found my own answer to my question.  In case anyone else reads this thread in the future:

The Ubuntu main Desktop CD isn't as flexible because it seems to require letting the install reformat the boot partition, but the Alternate CD gives a few install options for the bootloader, namely:
1. Install GRUB on the MBR (NOT what I want to do since I don't want to affect Boot Magic)
2. Install GRUB on the partition which I previously (during an earlier install step) directed as the /boot mount
3. Do not install a boot loader (i.e. leave my previous GRUB alone).

The Installer is not smart enough to edit an already existing GRUB menu.  So for my case, I could either do #2 above and manually add the previous GRUB menu entries (for my other OS(s)) after the Ubuntu install, or else do #3 and manually add the GRUB entry for Ubuntu after the install.  

The GRUB menu entries are in a file called /boot/grub/menu.lst.  For #2, manually make a copy of this file before the install, and afterwards use a text editor to merge the two sets of entries.

---

