---
title: "Defragmentation/Partition Creation in OS X"
date: 2011-03-30
forum: Apple Hardware Users
---

### Post by ransom630 on 2011-03-30
I'm trying to repartition the 60gb hd on my macbook 1,1 so that I can triple boot os x, ubuntu, and windows. When I try to repartition it all at once with diskutil resizeVolume, I get the error: "Resizing encountered error on disk disk0s2 gunton: No space left on device (28)" 

Everything I've found through google indicates that this means there is not enough contiguous disk space available to resize and create those partitions. I defragmented my harddrive using the online mode with idefrag, unfortunately that didn't work. I also tried boot camp to just do the windows partition first, but it says it that it cannot move system files or something, basically the same error as above.

My thought was whether or not I could either create an os x bootable cd (no dvd-r) and fully defragment it while it's offline, but a du -chs of the necessary directories was well beyond 700mb.

My next thought is the pertinent question: is there a disk defrag tool on the ubuntu live cd? if not, if i downloaded one and placed it on a usb drive, will it mount from the live cd? or is there another way to combat this partitioning problem that i'm unaware of? (i don't have an external harddrive, so i can't timemachine/reformat/restore system).

any help would be appreciated. thanks.

---

### Post by srs5694 on 2011-03-30
I don't know if there's a Linux HFS+ defrag utility, but there is a Linux partitioning tool called GParted that can resize partitions. I don't recall offhand if it's part of the Ubuntu live CD, but if not you should be able to install it by typing "sudo apt-get install gparted" in a Terminal window; or you could download [PartedMagic](http://partedmagic.com) or [System Rescue CD](http://www.sysresccd.org), both of which come with GParted. There are some caveats, though:


[list]
[*]If you've already used Boot Camp, the disk may be in [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) mode. If so, you're playing with fire. My recommendation is to use Linux's fdisk to check the disk's status -- "sudo fdisk -l /dev/sda" should show a single partition with "ee" under the "Id" column if the disk is *not* a hybrid disk. If it's a hybrid disk (with one or more partitions in addition to the "ee" partition), then you should make it a legal (non-hybrid) disk before using any Linux utility to resize partitions. You can do this with [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) by using the "n" option on the experts' menu.
[*]IIRC, GParted can only grow or only shrink HFS+ partitions, but I don't recall which way it goes. Thus, it's conceivable that it won't work for your purposes.
[*]Even if GParted can shrink HFS+ partitions, it's conceivable it will run into the same problems that the OS X Disk Utility did.
[*]There's always a risk when resizing partitions that something will go belly-up. Fortunately, OS X is less sensitive to certain problems than is Windows, but you should back up your OS X installation, or at least any critical personal data, before proceeding. (This applies whether you use GParted, Disk Utility, or anything else.)
[/list]


Another option is to create a bootable USB flash drive with OS X. I'm pretty sure this is possible, but I don't have step-by-step instructions.

---

### Post by conundrumx on 2011-03-30
I don't know of any reputable way to defragment HFS+ other than this:

Copy the entire contents of each partition off using Super Duper! or a similar method, then copy them back.  Resizing small disks is the only time HFS+ really *needs* defragging, lucky you.

---

### Post by ransom630 on 2011-03-30
Thanks for the clarification. I /would/ have just the right conditions for it to not be possible. Alas if I just had the cash for a new system, but hopefully I'll be able to get an external harddrive when I get paid next month to try the copy/reinstall/copy back method.

---

