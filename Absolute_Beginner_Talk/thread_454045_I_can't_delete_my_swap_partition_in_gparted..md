---
title: "I can't delete my swap partition in gparted."
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-05-25
I'm about to go insane. I've been feuding with this dual boot crap for the last six hours. Now I think I was on the right track and I wanted to redo my partitions, yet in gparted I can't delete my swap one.I figured ahh whatever, just create the ext3 and be done. But I can't create a partition in a filesystem. I can only create it as no file system on it. Empty space.

Whatever. How can I delete this swap partition? This is beyond ridiculous. "Invalid argument" is my error.

---

### Post by Kobalt on 2007-05-25
Are you sure that the disk you are trying to partition isn't mounted ?

---

### Post by Roasted on 2007-05-25
It's got a lock next to it. Yet I can't remove it.

---

### Post by Kobalt on 2007-05-25
Are you in a LiveCD session or a regular one ? The better is to start a session with a LiveCD in order to partition your drives.

---

### Post by Roasted on 2007-05-25
LiveCD.

---

### Post by Kobalt on 2007-05-25
Try ```
sudo umount -a
```Then lauch GParted again...

---

### Post by dptxp on 2007-05-25
Live CD uses the SWAP, you shall not be able to remove it with Live CD.

Download Gparted from their Website, it is an iso file like Ubuntu,burn to a CD, boot with it and Delete the SWAP.

You can make your partitions with that Gparted CD too. I had to make a SWAP partition before running Live CD, was giving problem with 192 MB RAM on one desktop.

---

### Post by Roasted on 2007-05-25
I got so pissed I just cut the power to the system and rebooted. Now I had the option to delete it. But I don't get this.

This is exactly what I do in gparted...

Leave NTFS alone...

Create 2gb SWAP
Create the remainder (207gb) EXT3

Then I apply changes.

After the installation process takes place where it installs Fiesty on SDA3, which is my 207gb EXT3 partition, I go into gparted to check it out. What I see is different.

Now I see NTFS - 25gb
Swap - 2gb
EXT3 (mountpoint - /target) 3.45gb
Unallocated - 203gb.

Why is 203gb being registered as allocated? EXT3 SHOULD BE THE 207GB! NOT JUST 3.45GB! That's EXACTLY how I set it up. Yet after I install Fiesty it registers this way. 


For what it's worth... my output of sudo fdisk -l







Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        3448     2096482+  82  Linux swap / Solaris
/dev/sda3            3449        3898     3614625   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+   5  Extended
/dev/sdb2              63       30515   244613722+  83  Linux
/dev/sdb5               1          62      497952   82  Linux swap / Solaris
ubuntu@ubuntu:~$



edit - I was just about to say whatever and reinstall windows AND linux, but I'm worried. WHY, OH WHY, is Gparted doing this to my partitions? I need to know that first.

---

### Post by Roasted on 2007-05-25
Here's the problem.

Whenever I apply changes to gparted, it mounts each volume that it is currently working on. I know this because windows pop up with the files showing that are in that volume. When it's all said and done, it's attempting to mount my windows partition and my ext3 partition. It cannot format i due to the fact it's mounted.

What I did was I left alone the windows partition, then I created the linux swap since I could create that without error. Then with the remainder of the allocated space, 207gb, being on sda3, I went into the command line and ran a sudo mkfs.ext3 /dev/sda3. I did this AFTER going to "computer" and unmounting EVERYTHING there. Then it installed ext3 just fine. Hmm?



New problem with the installer. It says I must mount a root point. What should the root point be? If I mount my ext3 partition as root, it resizes the ext3 partition to around 4 gig. Why? Should I have 3 partitions? Swap, root, and the remainder for ext3? Or what?

---

### Post by dptxp on 2007-05-26
Something is wrong somewhere. I had suggested you a neat way. But since you could wipe out swap you should have had no problems. Extra ext3 is not mandatory but recommended.

Reinstall. Retain NTFS. Delete all other partitions. Resize - 8 GB for /. Resize next space less 2 GB for ext3 and mount as /home. Last 2 GB as SWAP.

If you cannot with LIVE CD use the GPARTED CD first as I had suggested to make partitions.
Make sure to fomat (check the checkbox when installing from Ubuntu Live) all except NTFS.

And pray.

---

### Post by Roasted on 2007-05-26
Just as a follow up, that's what I did.

I ended up making 3 partitions on top of the NTFS partition already reserved for windows. Now my drive looks like this.

25gb NTFS
2gb SWAP
13gb ROOT
200gb HOME

All good and running well. :)

---

