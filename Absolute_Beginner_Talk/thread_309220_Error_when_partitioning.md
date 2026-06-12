---
title: "Error when partitioning"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by KentS on 2006-11-29
I'm currently trying to install Ubuntu in a dual boot system with Win XP on a HP Pavilion dv2004ea. My laptop is new, bought less than a week ago. Nothing has been installed. 

The laptop has a 80 GB hard drive with 2 partitions. One "Local Disc" with NTFS. Its total size is 66.2 GB, with 57.6 GB available space. The other partition is "HP Recovery" with FAT32. Its total size is 7.20 GB and has 1.20 GB available. I used GParted and it seems the HD has some MB outside the partitions and one last small partitions of about 1 GB (Buffer?).

I ran Scan Disc and Disc Frag. All files were moved to the beginning of the HD, except from some not moveable. However all files are in the first 1/4 of the HD. I inserted the Desktop CD and rebooted the system, choosing installation after Ubuntu had loaded. I then chose to manually edit the partition table, and tried to resize the NTFS partition to 20, 25 and 30 GB, respectively. Every try resulted in an error, not specifying any reason. I then tried with the Alternate CD. Typed in new size for partition, pressed forward. Nothing changed.

What can I do?

I see a forum member called moshuptrail sais that this might be due to bad blocks in my NTFS partition. Is there any way I can confirm that? Considering that this is a completely new PC, unaltered after purchasing, can this me a manufacturing error enabling me to return the PC?

moshuptrail also recommends ntfsresize for those who are not faint harted. Are there any other way than having to use ntfsresize?

---

### Post by ajgreeny on 2006-11-29
Download the new version of gparted liveCD and boot to that.  It is great for partitioning (like partition magic) your hard drive and will give you a good clue if anything is wrong with the partitions.  You should find that when you get to install the system, if you chose the option to use free space on the disk, you will then be able to set your ubuntu partition size at that point.

Alternatively use the alternate install CD (text based) which gives you more options.

---

### Post by KentS on 2006-11-29
Okey, I've downloaded gparted live and ran it. When trying to resize my windows partition I was informed that the minimum size for the new partition is 67884 MB and the maximum 69892. The last number might have been a typo. I guess it should be 67892, but I include both versions. When using the Dapper Drake CDs, the min size was around 8500 MB.

So I ran defrag three more times in a row. And I'm still being informed that the min. size is 67884 and the max size is 67892.

Any ideas what I can do now?

I don't know if windows is mounted to the partition, and if I have to unmount it before being able to partition my HD. I do not know how to unmount windows.

Thank you for your help.

---

### Post by jrev on 2006-11-29
No need of the gparted live CD ...

You just boot on the normal Ubuntu 6.06 Dapper live+install CD 

When on the Desktop, menu applications/Accessories/Terminal

type : sudo gparted 

When you see your partitions they are unmounted so you can reduce them according to what you see on the screen

you can see the size of the busy part of every partition

---

### Post by KentS on 2006-11-29
I tried to do that. The program tells me that only 8.63 GB of the partition is in use. When I try to apply the changes I get a non specified error. The error says:
"Error while resizing/moving /dev/sda1
Be aware that the failure to apply this operation could affect other operations on the list."
This is equivalent to when I used the Desktop CD.

On the terminal I get a lot of output saying
"Error reading inode 29"
"Error reading inode 536"
and so on.

I also get some output saying
"Warning: Unable to open /dev/hdc read-write (Read-only file system). /dev/hdc has been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label."

All this output was repeated twice. I tried to resize the HD again. The program freezed and the output on the terminal was
"xlib: unexpected async reply (sequence 0x6f5b2).

---

### Post by KentS on 2006-11-29
It helped to run ScanDisc one more time.

Thanks for your help

---

