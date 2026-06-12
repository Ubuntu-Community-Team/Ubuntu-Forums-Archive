---
title: "AutoMount OSX and Enlarge Ubuntu Partition...HOW?"
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by hananias on 2008-07-01
I have a dual boot Macbook 180g partition (I don't know generation, maybe 1st)...Ubuntu (30g) is running great, and also looking great.  I also have some nice programs I installed that I don't want to lose.  My question is a 2 part question...

I want to enlarge the Ubuntu partition.  I have about a little over 80gigs left of unallocated space.  My Mac can't see that partition, but Ubuntu can...I want to take that and split it in half and add to each partition.  but I seem not to be able.

Then that takes me to another question, when using Ubuntu I want to use my music, movies, and pictures folders with out having to go into My Computer and mount the drive manually each login.
I don't have problems reading my files, I just want them ON, always.  Any advice is greatly appreciated!  Thank you in advance.

---

### Post by logos34 on 2008-07-01
can you post your partition table?

sudo fdisk -l

---

### Post by cyberdork33 on 2008-07-01
there really aren't any applications that can "grow" an hfsplus partition outside of OSX.

You should be able to resize your Ubuntu partition with gparted and livecd.

---

### Post by hananias on 2008-07-02
Here's the report from fdisk

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26       31387   251906988   af  Unknown
/dev/sda3           31387       38914    60459399+  83  Linux

Well, The "unknown" partition is the main osx.  I want to be able to automount my drives to each other.  Mainly I want my OSX in Ubuntu to start up automatically.  Now I copied over my music and pictures, but you understand that I like to save those gigs if I could.  How can I go about?

---

### Post by logos34 on 2008-07-02
try this:

**sudo parted**

**print**

What does it show?

For the rest, try the methods in these links:

[http://www.mactel-linux.org/wiki/HOWTO#HDD_partitioning](http://www.mactel-linux.org/wiki/HOWTO#HDD_partitioning)
[https://help.ubuntu.com/community/Intel_iMac#Partitioning%20with%20the%20commandline](https://help.ubuntu.com/community/Intel_iMac#Partitioning%20with%20the%20commandline)
[http://ubuntuforums.org/showpost.php?p=2346494&postcount=1](http://ubuntuforums.org/showpost.php?p=2346494&postcount=1)
[https://help.ubuntu.com/community/Fstab#More%20Examples%20of%20Entries](https://help.ubuntu.com/community/Fstab#More%20Examples%20of%20Entries)
(->'HFS+')

Good luck

---

### Post by hananias on 2008-07-03
thanks all for the advice.  i'll post back with some results

---

### Post by oswaldkelso on 2008-07-03
Why not clone your 30gb ubuntu partition on to the free 80gb.

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

Then if all goes well delete your 30gb partition.

---

### Post by BuffaloBill on 2009-06-10
Any tips for the automount at startup?  I found this [[COLOR="Red"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=451987") in the forums but it's read only and I'ld like comments about the procedure.

---

### Post by cyberdork33 on 2009-06-11
> **BuffaloBill said:**
> Any tips for the automount at startup?  I found this [[COLOR=Red]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=451987") in the forums but it's read only and I'ld like comments about the procedure.
You can add the partition to your /etc/fstab file to automount... the read-only thing is another issue entirely. Linux does not support read/write on journalled HFS+ partitions, and I wouldn't recommend disabling it on your main osx partition as it is there to prevent file system corruption.

---

### Post by BuffaloBill on 2009-06-11
Thanks cyberdork33, I already use my Mac partition's files to listen to music and stuff.  But you're right about not modifying the privileges in your Mac partition.  I wouldn't recommend it either :)

The only thing I was looking for was about the auto-mount thing...  I'm not that familiar with the fstab file and just wanted to be sure about the manoeuvre.

---

### Post by cyberdork33 on 2009-06-11
> **BuffaloBill said:**
>  The only thing I was looking for was about the auto-mount thing...  I'm not that familiar with the fstab file and just wanted to be sure about the manoeuvre.
It looks like that thread you linked to has that covered.

---

