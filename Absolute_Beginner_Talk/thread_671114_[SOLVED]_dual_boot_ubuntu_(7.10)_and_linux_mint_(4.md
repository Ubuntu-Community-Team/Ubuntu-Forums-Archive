---
title: "[SOLVED] dual boot ubuntu (7.10) and linux mint (4.0)"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-18
I heard good things about Linux Mint so decided to give it a try.
The LiveCD is painfully slow, so I want to dual-boot with my current Gutsy install and share my data between the two.
My HDD is partitioned as follows: about 17 GB for /, about 215 GB for /home and about 2 GB for swap.
I was thinking I could take out about 7 GB from the /home to install Mint.
I've never dual-booted before, installing Ubuntu was the only time I've ever installed an OS. Could someone tell me how to go about this?
In particular, could Ubuntu and Mint share the swap partition or do I have to make a separate one for Mint? And how do I share my data between the two? (I know it is possible to share the same /home partition, but won't the settings clash?)
Any opinions about Mint in general are also welcome.
Thanks.

---

### Post by ajgreeny on 2008-01-18
Mint 4 is great.  I triple boot Ubuntu 7.10, Mint 4 and windows XP, though on two disks, not just one, but that won't make any difference.  I also have separate homes for each and use each one as a backup of the other, being separate disks it seems an extra safety backup.

The mint install will find your Ubuntu and put it on the menu for grub without problem, so no difficulty there.  As for a shared /home, that shouldn't be a problem with those two versions of Ubuntu and Mint, as they are basically the same and use the same repositories, except for the few Mint apps.  Problems could appear however, when and if you update one to the next version without the other being updated.  You could either make a new /home for the new one at that point, or wait until both distros have been updated together, before doing either update process.  Your choice, but if it were me, I would give it a try now and sort out any problems on updates later, when a new version appears.

---

### Post by kleo skywalker on 2008-01-19
Thanks ajgreeny.
The updates are not an issue. I want to try Mint for a while. If I like it, I'll switch to it. If not, I'll delete it and stick with Ubuntu.
What I'm looking for is a guide to pull out space from a partition, and dual-boot with Mint sharing my /home. I've never done this before, and am afraid to mess up.

---

### Post by kellemes on 2008-01-19
Don't share your /home would be my advise..
I wonder why you have such a large /home for Ubuntu..
I'll tell you my setup, I'm running triple boot..

- one hd (hda) for Windows.
- one hd (sda) for filestorage, 500Gb formatted ext3.
- one hd (sdb) partitioned for 2 GNU/Linux-distro's as follows..

sdb1 - ext3 - 500 Mb   used as /boot for dist-1
sdb2 - extented partition (needed so I can make the many partitions I want)
sdb5 - swap - 1Gb       used as swap for **both** distro's.
sdb6 - reiserfs - 4Gb   used as /var for dist-1
sdb7 - ext3 - 10Gb      used as / for dist-1
sdb8 - ext3 - 20Gb      used as /home for dist-1
sdb9 - ext3 - 500Mb    used as /boot for dist-2
sdb10 - ext3 - 10Gb    used as / for dist-2
sdb11 - ext3 - 20Gb    used as /home for dist-2

This is just my way of doing things.. you need to find yours..
You can obviously stick to your own partition-scheme and filesystems.

When installing another distro it'll probably overwrite your bootloader, that's no problem, you can use [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) to restore your Grub-install from your previous installed distro, or manualy fix things if needed.

---

### Post by kleo skywalker on 2008-01-19
kellemes, thanks for your post - most of it is too complicated for my needs though!
I have only one 250 GB SATA HDD, and only one OS on it - Ubuntu 7.10. That should explain the large /home - it's where all my documents, music, photos and such like live.
I like Ubuntu, but I am kind of weary of Quicktime videos not working and things like that. So when I heard that Linux Mint does stuff of that sort without me having to fix anything, I decided to give it a try.
The only reason I need to dual-boot it with Gutsy is that the LiveCD is way too slow. I want to install it to my hard disk, use it for a few days and then decide which one I want to keep  - Ubuntu Gutsy or Mint Daryna. (I intend to keep only one OS.)

Why do you advice not sharing the /home?

---

### Post by Moop on 2008-01-19
I wouldn't recommend sharing your home directory either. Home is where many of your configuration files are stored. You will still be able to access your files from the new install. 

If you're just trying out Mint don't bother with a separate home partition. Shrink your old home partition to create some space and then create a partition from the empty space to install Mint to.

You only need one swap partition. Remember that you are limited to four primary partitions so plan accordingly.

---

### Post by ajgreeny on 2008-01-19
As I hope I intimated when I answered your original question, I would not normally tell anyone to share their /home partition with another distro, but with Mint 4 being basically the same as ubuntu 7.10, I don't think it will give you any problems with the OS itself, which should be fine.

There may, though, be difficulties with your config settings for things like themes, etc etc, which will not be available to both OSs.  Therefore, on reflection, I think I would have to agree with the other posters;  keep your /home partitions separate for the two systems and when you've decided which OS to keep, just sort out the old partition space with gparted, and add it to whichever current partition you want to, or keep it as a separate partition for data.

---

### Post by kellemes on 2008-01-19
> **kleo skywalker said:**
> kellemes, thanks for your post - most of it is too complicated for my needs though!


I understand, I just presented my theme to give an example..
But especially when you want to dual boot you better think of a well prepared partition-scheme..
You can make it as simple as possible.. ;-)

You can give each of the distro's a /(root)-partition and a /home-partition and use **one** swap partition for both.

So 5 partitions to get 2 distro's running.
Personally I like to keep my filestorage separate from the rest, this is for backing-up stuff and the storage of data I want to be able to **not touch** when reinstalling, adding or removing distro's.

About a shared /home-partition..
Why would you want this?

---

### Post by kleo skywalker on 2008-01-20
Thanks all.
I asked about sharing /home because I wanted to confirm if settings would clash or not. This is now clearer to me; it's unnecessary if I can access my data from Mint without sharing the partition.
So I'm going to go with Moop's suggestion - pull out some space from my /home and install Mint on it.
To pull out this space, I need the GParted Live CD, don't I? Is there a GParted guide or tutorial that someone could point me to? I have no idea how to use it. (Actually, I also want to back up my install, and someone recommended the GParted-Clonezilla Live CD.)
Thanks.

---

### Post by cjm5229 on 2008-01-20
Both Mint's Live CD and Ubuntu's Live CD have gparted in them it is System>Administration>Partition Editor. You have to be sure and unmount the partition you are changing, The icon on your desktop for that partition can be right clicked then click unmount. Sometimes gparted won't unmount the drive itself. PCLinuxOS and Knoppix both have excellent partitioners also. I have found that trying to dualboot 2 Ubuntu based Distros with a shared /home will mess up your fstab and you won't be able to boot into the first OS because it can't find /home. The uuid number gets changed and can be a real pain to fix.
To fix your video issues just install "Ubuntu restricted extras" Add/Remove>Other and "non-free codecs" in Synaptic, then just make sure all the gstreamer codecs are installed, Add/Remove again. VLC, Ogle, and Mplayer can play anything you will find. 
Good Luck. Carl

---

### Post by kleo skywalker on 2008-01-24
So I shrank my /home partition using the GParted LiveCD, and installed Mint on it. Nothing went wrong.
All the talk about sharing /home was because (having never dual-booted) I didn't realize that the other partitions on the hard disk would be automatically mounted and accessible from my desktop.
I like Mint so far, if that doesn't change in a few days I'll probably switch to it.
Thanks all.

---

