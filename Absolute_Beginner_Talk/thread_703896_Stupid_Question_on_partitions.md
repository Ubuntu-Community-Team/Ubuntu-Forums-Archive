---
title: "Stupid Question on partitions"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by umontu on 2008-02-21
Hey If i have ubuntu running and i decide to have a new partition to run windows and i make one in fdisk will it delete my current partition?

Can someone just explain it to me Ive been searching for over an hour now but Ive not seen anything on this

---

### Post by em3raldxiii on 2008-02-21
If you have a large area of continuous free space on your existing partition, then you can often resize that partition (only by truncating the END, not by shrinking the beginning of the partition).  Then in the newly "unpartitioned" space, you can add a new partition and format it however you like.

However, if you go to install Windows on that partition, the windows installer is stupid, and it will overwrite your existing boot manager.  In other words, no GRUB.  So you will then have to use your Ubuntu disc (or some other linux disc) to reinstall GRUB.

---

### Post by GSF1200S on 2008-02-21
Do you currently have windows installed?

Please post the results of:

sudo fdisk -l

If you change the partitions, or repartition to include windows, youll need to edit your menu.lst or install grub from a liveCD...

---

### Post by umontu on 2008-02-21
nope i had it before ubuntu though

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd183d183

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9777    78533721   83  Linux
/dev/hda2            9778        9964     1502077+   5  Extended
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris

Another question If I wanted another linux os on my pc would that be easier than windows to install?

---

### Post by em3raldxiii on 2008-02-22
I've never done specifically that (install an alternate version of Linux alongside Ubuntu), but a handy thing you can do is share /home folders between Linux installations if you have it on it's own partition.

---

### Post by bumanie on 2008-02-22
If I were you I would download gparted and use that to partition your drive. It is very much like the tool on the ubuntu live cd, however it's only function is to partition drives, ie it is a specialized tool.
It is much easier to install windows first, because it prefers a first partition on a hard drive. It is not impossible to boot windows from a non-first partition, but it will make the task of getting a dual boot machine operating correctly somewhat more difficult. Get gparted from here [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
and if you have problems with grub after the install read this [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
If you are fairly new, I would tend to advise you start from scratch and install windows first, followed by ubuntu. If you decide to install another linux distro. there should not be a problem with grub and you can share the same /swap and /home (usually without problems), you will only need to make a / for the other linux. (at  least that's how it should work)
PS: No question is stupid.

---

### Post by Moop on 2008-02-22
Installing another version of linux along side of Ubuntu will work fine and you won't have the problem of overwriting grub like you do with windows. 

Sharing a home partition between distros isn't a good idea. The configuration files are going to be different and I don't see how that would work. You will still be able to access  files in your ubuntu install from the new distro. :guitar:

---

### Post by bumanie on 2008-02-22
You could be right re incompatibility with shared home on different linux, however, I know of some people who have done it with no problem, whilst others have had problems. It doesn't seem to be a hard and fast rule. Never really looked it the why's and why nots, as I have only used ubuntu in that manner ie 2 different versions. There are some who say that doesn't work either, but I have never had an issue.

---

### Post by louieb on 2008-02-22
Just looking at the fdisk output. The simplest way to go: use [GParted]("http://www.sysresccd.org/Main_Page") and shrink hda1 by 10-15GB. You will now have unallocated space. Click on it and create a primary partition in that space. If you want to install windows format it NTFS - if you install another Linux distro doesn't matter what (the Linux installer will reformat it the way it wants).

2 cents: sharing a home partition = weird problems (sometimes).

If you install windows. You will have to change the IPL (inital program load) in the MBR back to GRUB. Thats easily done.  [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
Good luck.

---

