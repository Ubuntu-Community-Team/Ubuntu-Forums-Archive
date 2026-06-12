---
title: "Argh! How to install Ubuntu over old Linux dual boot?"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by bigkahuna on 2006-01-13
I'm having "one of those days" I'm sorry to say (I guess it being "Friday the 13th isn't helping):

I've got a system that is currently running dual boot Windose XP Pro and Kanotix (Debian Sid) and Grub was set up as the boot manager.  My Kanotix install is old and having problems and I thought now would be a good time to try out Ubuntu 5.10.  So I want to just replace the Kanotix install (that resides on a 4 gb partition with another 500 mb linux swap partition) with Ubuntu.

I searched the forum here, the wiki and booted the disk a number of times but never found an easy way of doing it.  So I thought that I'd just get rid of the Linux partitions entirely and start all over.  No luck, the only way I've found to fix the MBR is with a Windows boot disk, and my only XP Pro boot disk is corrupted :(  (BTW, I don't have a floppy drive in this system, so I can't use any of the 3rd party boot floppies.)

So I'm stuck, I really don't want to go out and buy a new set of XP disks (ouch!) just to be able to install Ubuntu.  Isn't there an easier way?  Can't I  get Ubuntu to just install on top of the Kanotix partition and edit GRUB?

Can someone please help?

---

### Post by Herman on 2006-01-13
> I've got a system that is currently running dual boot Windose XP Pro and Kanotix (Debian Sid) and Grub was set up as the boot manager. My Kanotix install is old and having problems and I thought now would be a good time to try out Ubuntu 5.10. So I want to just replace the Kanotix install (that resides on a 4 gb partition with another 500 mb linux swap partition) with Ubuntu.
So I thought that I'd just get rid of the Linux partitions entirely and start all over. No luck, the only way I've found to fix the MBR is with a Windows boot disk... You should be able to just use the partitioner in the Ubuntu 5.10 install disk. When it gets to [!!] partition disks, and you select 'manually edit partition table', can you select your old kanotix partition and select 'delete the partition'?
Normally, that should be all you need to do. Then you should see 4.0 GB free space to install Ubuntu on. If you want you can delete the swap too, and let Ubuntu automatically partition the free space. Or, you can just leave the swap partition alone and create a new partition in your 4.0 GB free space and make it ext3 or reiserfs file system, make it for mount point /, and stick the bootable flag on it. Then choose 'done setting up the partition', and 'write changes to disk'. The rest of the Ubuntu install should follow quite easily. 
I hope this helps,  :D (Herman).

---

### Post by Digitallysick on 2006-01-13
i would think you could go into safemod, dos prompt only and fixmbr. (to clear grub) then you can install ubuntu over the old linux os. ( anyone here correct me if im wrong?)fixmbr fixboot.

---

### Post by jimrz on 2006-01-13
[**[COLOR="Sienna"]Here[/COLOR]**]("http://users.bigpond.net.au/hermanzone/") is an excellent guide to doing an ubuntu / xp dual boot. Boot from the ubuntu install cd, when you get to the partioner choose "manually edit the partion table", then select your current linux partition(s) to be formatted and used for /, /home and swap, the intaller will also detect your win xp and give you a fresh GRUB to boot from.

Welcome and good luck.

---

### Post by bigkahuna on 2006-01-13
Unfortunately, things are not that easy:

1.  You cannot use fixmbr on the same disk that you have booted from.  You have to boot from a different disk (usually a CD or floppy drive) to do this, or so I've learned from the M$ website.

2.  No, there isn't an option in the Ubuntu installation to "erase" a partition or to copy over a partition.  It only allows you to:
  a.  erase the entire disk and use it for linux
  b.  repartition and use a portion of an existing partition for linux

3.  Yes, that's a great tutorial, and I've already gone through it, unfortunately I'm not sure how it applies to my particular situation.  Could you please give me a bit more info?

---

### Post by Herman on 2006-01-14
> 2. No, there isn't an option in the Ubuntu installation to "erase" a partition or to copy over a partition. It only allows you to:
  a.  erase the entire disk and use it for linux
  b.  repartition and use a portion of an existing partition for linux
3. Yes, that's a great tutorial, and I've already gone through it, unfortunately I'm not sure how it applies to my particular situation. Could you please give me a bit more info? The 8th illustration on each of the three example installs on the Ubuntu dual boot site (hermanzone), all show four options:

[COLOR=#000000][FONT=Arial]Resize IDE1 master, partition #1 (hda1) and use freed space
Erase entire disk: IDE1 master (hda)- 30.0 GB....(etc)
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Erase entire disk abd use LVM: master (hda)- 30.0 GB....(etc)
[COLOR=Sienna][B]Manually Edit Partition Table

[/B][/COLOR][/FONT][/COLOR]You select 'Manually edit Partition table', and the next thing you should see is a list of all your current partitions. You should see your old Kanotix partition on that list somewhere. If you select that line that describes you old Kanotix partition and press enter, you should see an option there somewhere to 'delete the partition'.
Try agian and see if you can see it this time... unless your computer is a little different or something is wrong, you should be able to see that. I hope this helps you.. (Herman):smile:

---

### Post by Mr_Grieves on 2006-01-14
I did like this.

1) Resized my XP partition in XP, using the Disk Manager (Administration tools).
2) Put in a Ubuntu Breezy CD.
3) Let Ubuntu notice that "Hey there! You quite some room where I may reside  boy!"
4) Looked very happy.

---

### Post by steve.horsley on 2006-01-14
I don't quite understand what your problem is. You don't need to fix the MBR if you're about to reinstall GRUB. 

The only problem I can think that you will have is that the Ubuntu installer refuses to install over a working system partition. I found this when trying to install Ubunto over Mandrake. I eventually had to use a live CD delete all the files on the partition that I wanted to re-use before the Ubuntu installer would admit that there was a suitable partition to install onto.

---

### Post by bigkahuna on 2006-01-14
Well looks like I was making a big fuss over something that ended up being alot easier than I thought!

I'd forgotten that I have a copy of "Boot Magic" that came with a copy of "Partition Magic" I purchased last year.  I used that and replaced GRUB (but I don't think I even needed to do that).  Then I used Partition Magic to delete the old Linux partitions.  Then when I booted with the Ubuntu install disk, I followed the manual installation and just installed Ubuntu to the empty spot on the HD.  Then I let Ubuntu install GRUB to the MBR (I didn't understand / want to take a chance with any of the other boot options.  I'ved edited GRUB settings before, so I can go back and change that later.)

Bottom line:  I'm writing this reply from my fresh Ubuntu 5.10 install :)  Boy, Ubuntu is -very- different from Debian/Kanotix!  It'll take a while for me to get used to this...

THANKS VERY MUCH to all who helped me!  This is a wonderful community and I appreciate all your help!

---

