---
title: "Grub error 2, occured after screwing up partitions"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by adampyre on 2007-05-27
Hello,

I have a laptop that I originally had Windows XP on. I installed Ubuntu on it to try it out a few months ago and loved it, so I decided to give Ubuntu the majority of free space and after research it looked like GParted was the way to go. So I burned the Live CD and started messing with my partitions. I wanted to get rid of XP, but I need the TV Out feature for watching downloaded movies and shows, and even with the ATITVOUT option, the picture didn't look right and I haven't had time to try and tweak it. So basically all I use XP for is watching stuff on my tv, Ubuntu for everything else. Any, getting off track....

THE PROBLEM:

I was using GParted, and in the middle of growing the Ubuntu partition, my laptop battery died! It's my fault for not plugging it in and paying attention to this...... well, instead of trying to boot Ubuntu after this happened to check if it was ok, I went right back into the Live CD for GParted and continued the operation of growing the Ubuntu partition. It checked the partition for errors and grew it and then I rebooted and was confronted with a Grub Error 2. I have been looking around for a fix but can't seem to find one for my situation. Any suggestions on getting Ubuntu back? Thanks.

---

### Post by Happy_Man on 2007-05-27
According to Google, a GRUB Error 2 means your BIOS doesn't recognize the presence of a filesystem:
> 2 : "Selected disk doesn't exist"
 This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

I'm not a BIOS genius, so I can't help much more than that.... still, knowledge is power, right?

---

### Post by adampyre on 2007-05-27
Does this mean the disk isn't bootable anymore? Hmm... an MBR fix maybe?

---

### Post by adampyre on 2007-05-27
I tried doing a grub-install fix from the live cd but it won't recognize anything. Any other suggestions?

---

### Post by adampyre on 2007-05-27
Bump.

---

### Post by adampyre on 2007-05-27
Apparently the is a program, "Super Grub Disk" that might be able to help me with this but I am having trouble finding a good link I can download this at. Anyone ever hear of it? Plus I am trying to do this from Windows on another computer, as Linux won't boot..... thanks...

UPDATE: I found a link. Never mind!I will post back here if it helps, hopefully helping people with grub Error 2 in the future...

---

### Post by alienexplorers on 2007-05-27
[http://freshmeat.net/projects/supergrub/?branch_id=62132](http://freshmeat.net/projects/supergrub/?branch_id=62132)

---

### Post by adampyre on 2007-05-28
Well, using the Super Grub disk I am able to boot windows, but not Ubuntu :( and it doesn't seem to help with fixing Grub error 2.....

---

### Post by adampyre on 2007-05-28
I will marry whomever can help me fix this. I can cook and do dishes. You'll just have to deal with my hairy back and toes.

---

### Post by adampyre on 2007-05-28
PS... I refuse to accept a re-installation of Ubuntu as being the answer to this problem. I really really really want my configuration back. I spent hours and hours and hours tweakign it just right with Beryl and packages galore. Plus I already had a few important documents. I don't care how technical the answer is, I am willing to try anything!... :p 

Thinking cap time.

---

### Post by freebird54 on 2007-05-28
I would be trying to 'see' it from the Live CD, and if I can see, it I would mount it and run fsck on it.  As far as I can tell- Grub error 2 means that the system can't even see where a valid drive/partition is.

If you CAN'T see it, you have to assume that the partition data is not currently written on the info section of the drive (first 512 bytes I seem to remember).  IN this case- hope you remember EXACTLY what you had for partition size and so on before you started.  If you can 'build' a copy of what OUGHT to ge there, you can use dd to copy this build onto the start of the drive, and the partition should magically appear.  One way to do this is to set up the same partition table on an unused drive of the same spec. and dd the first 512 off the drive for storage, and restoration to yours.  Try 2 would be to set up the INTENDED partition setup, and dd that for restoration (hard to know at what point the process actually died).

Most people seem to have just reformatted to fix it - so there's not much help out there in Google land that I can see.  Here's a link with some info on using DD to play with boot sectors etc (and to back up boot sectors as well) that might get you started.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)  -  look for the section on backup and restore of your MBR.

Hope that leads to a solution!

If the drive is only partially corrupted, it may be a bit simpler - only need to set the correct limits for the actual partition then - still easiest done with a limited dd - specifying how many bytes to what offset.  Hope you can follow what I mean here!

---

### Post by odiseo77 on 2007-05-28
ok, since this seems to be an issue with a messed partition, and you can boot windows, try running [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Download") from windows (download the windows zip file, extract it and then execute the testdisk_win.exe file (if you're running a windows version older than windows 2000, you'll need the TestDisk DOS version)). Hopefully, it will detect your ubuntu lost partition and write it to the partition table :-)

---

### Post by alienexplorers on 2007-05-28
Can you post the output of 
> sudo fdisk -l

---

### Post by adampyre on 2007-05-28
> **alienexplorers said:**
> Can you post the output of

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         481     3863601    7  HPFS/NTFS
/dev/sda2   *         482        2371    15181425   83  Linux
/dev/sda3            2372        2432      489982+  82  Linux swap / Solaris

Disk /dev/sdb: 519 MB, 519569408 bytes
255 heads, 63 sectors/track, 63 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          64      507360+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(62, 254, 63) logical=(63, 42, 43)
ubuntu@ubuntu:~$

---

### Post by alienexplorers on 2007-05-28
Put your windows disk in and boot into recovery mode and enter Fixmbr & fixboot.  Next put your live cd in and type in terminal:
> sudo grub
find /boot/grub/stage1
root (hd#,#)
setup (hd#)

the # signs should be replaced with the data from the find /boot/grub/stage1 output.

---

### Post by Herman on 2007-05-28
Hello adampyre,
According to the Gnu Grub Manual 0.97, which is the current version of Grub that Ubuntu uses, (as opposed to Erich Boleyn's  [Original GRUB documentation]("http://www.uruk.org/orig-grub/") for version  0.5 which is not the Grub we are using these days),
> 2 : Bad file or directory type
This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.I would try a file system check first. Since you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/")  you could just right-click the partition and click 'check', and GParted LiveCD will run 'e2fsck -y -f -v /dev/sda2' for you. Be sure to click on the 'Details' button as many times as you need to to get all the details, they might help.
If your file system was really bad it would have had a black rectangle around it in GParted instead of a colored one, and you would have noticed that and mentioned it in your post, so I don't think it's something impossible to repair.
If it does have the black rectangle and the file system check doesn't fix it then I'm not so optimistic, sorry.
Or you could run 'e2fsck -y -f -v /dev/sda2' from the Ubuntu Live CD as long as that file system is not mounted yet, ```
e2fsck -y -f -v /dev/sda2
```Your partition table looks okay according to your fdisk output, there's nothing to fix there.

It the file system check goes okay and the partition looks healthy, we could try taking the error message literally and try a direct boot from Super Grub Disk's [Grub Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to try to boot your kernel and initrd.img directly rather than through the symlinks just in case that helps. Here's a link to that particular spot on that page, [Direct Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). Actually, even that method boots the kernel through the symlink, but at least it's interactive. In most (but not all) computers you will see some feedback from Grub letting you know what's going on. That can be very helpful in diagnosing and solving booting problems. Let us know how you are getting along.

I hope one of these ideas will help you,
Regards, Herman :D

---

### Post by adampyre on 2007-05-28
Hey Herman,

I did the check with GParted (not a black box by the way) and it did find several errors and fixed them. The interesting thing is that even though i only run the check, it attempts to grow the partition, but then says there is nothing to be done?

Anyway, I also made the Ubuntu partition  bootable, and now after post initialized and it tries to pass of to the kernel, instead of grub or anything, I get

1234F:_ 

(the underscore denotes a blinking cursor)

I can hit enter and get a column full of those but it won't let me type anything else.

I'm going to keep messing around with the various things mentioned in this post, but does the 1234F: mean anything? Like 1234Forget it, reformat and reinstall? ;)

I hope not. :p

UPDATE:

I am finding that if I press 1, it boots into Windows (my first partition). 2 Must represent my Ubuntu partition, but when I press 2, I get NADA. 3 must be the swap and 4 must be the pen drive I have hooked up. F must be floppy, because it takes a minute and then reprints the 1234F: menu to the screen after I press it (I don't havea a floppy drive on this laptop.) Anyway, my Ubuntu partition isn't bootable apparently? 

> **Herman said:**
> Hello adampyre,
According to the Gnu Grub Manual 0.97, which is the current version of Grub that Ubuntu uses, (as opposed to Erich Boleyn's  [Original GRUB documentation]("http://www.uruk.org/orig-grub/") for version  0.5 which is not the Grub we are using these days),
I would try a file system check first. Since you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/")  you could just right-click the partition and click 'check', and GParted LiveCD will run 'e2fsck -y -f -v /dev/sda2' for you. Be sure to click on the 'Details' button as many times as you need to to get all the details, they might help.
If your file system was really bad it would have had a black rectangle around it in GParted instead of a colored one, and you would have noticed that and mentioned it in your post, so I don't think it's something impossible to repair.
If it does have the black rectangle and the file system check doesn't fix it then I'm not so optimistic, sorry.
Or you could run 'e2fsck -y -f -v /dev/sda2' from the Ubuntu Live CD as long as that file system is not mounted yet, ```
e2fsck -y -f -v /dev/sda2
```Your partition table looks okay according to your fdisk output, there's nothing to fix there.

It the file system check goes okay and the partition looks healthy, we could try taking the error message literally and try a direct boot from Super Grub Disk's [Grub Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to try to boot your kernel and initrd.img directly rather than through the symlinks just in case that helps. Here's a link to that particular spot on that page, [Direct Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). Actually, even that method boots the kernel through the symlink, but at least it's interactive. In most (but not all) computers you will see some feedback from Grub letting you know what's going on. That can be very helpful in diagnosing and solving booting problems. Let us know how you are getting along.

I hope one of these ideas will help you,
Regards, Herman :D

---

### Post by adampyre on 2007-05-28
Hey,

I did the fixmbr and fixboot on the partition. Now, when I try boot the Ubuntu partition, instead of 1234f:, i get NTLDR missing, press any key to restart. 

I also tried the grub thing from the ubuntu live cd, but when I do "find /boot/grub/stage1" I get:

Error 15: File not found.

The drive wasn't mounted. I'm still new, so please excuse any ignorance on my behalf. I mounted it, mount point was /media/disk. So I thought I'd try find /media/disk/boot/grub/stage1 and I still get the Error 15 

> **alienexplorers said:**
> Put your windows disk in and boot into recovery mode and enter Fixmbr & fixboot.  Next put your live cd in and type in terminal:


the # signs should be replaced with the data from the find /boot/grub/stage1 output.

---

### Post by adampyre on 2007-05-28
UPDATE:

Apparently the 1234F: menu is from TESTDISK that I used to try and fix this. I had it write it's own MBR to the disk and this is from testdisk....

---

### Post by freebird54 on 2007-05-28
When you did your fdisk - it claims that the physical and logical ending for the partition are different.  Look in the grub page again - and there should be a section about the 2 copies of the partition table not agreeing with each other - and how to make them agree.  I suspect the cure (if possible) lies within that area... a partially completed resize operation.

If not that  - then try to get the logical and physical value to match up.  dd the current boot block to a file, try changing the relevant values and dd it back and see where you are....

Scary stuff to 'play' with though!

---

### Post by adampyre on 2007-05-29
Thanks for the suggestion. I'll try it. Scary to play with, yes, but I'm willing to do anything as a last resort to just reformatting, which I will probably end up doing anyway. I just know there has to be a solution. Thanks! I will update.

> **freebird54 said:**
> When you did your fdisk - it claims that the physical and logical ending for the partition are different.  Look in the grub page again - and there should be a section about the 2 copies of the partition table not agreeing with each other - and how to make them agree.  I suspect the cure (if possible) lies within that area... a partially completed resize operation.

If not that  - then try to get the logical and physical value to match up.  dd the current boot block to a file, try changing the relevant values and dd it back and see where you are....

Scary stuff to 'play' with though!

---

### Post by adampyre on 2007-05-29
Well, I messed around with everything mentioned in every post but unfortunately due to me being to green at this stuff right now, I think I made it worse. I ended up corrupting the partition!

So, as we speak, I am re-installing Ubuntu to my laptop. Not losing anything I can't live without. Keep all the important stuff on my pen drive. Thank you to all the people who tried to help! If a MOD wants to  delete this thread since it's not very useful, feel free! Hate to muck up this site any more with more useless drivel from me :p

Thanks!

---

