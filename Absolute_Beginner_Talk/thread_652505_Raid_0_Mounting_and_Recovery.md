---
title: "Raid 0 Mounting and Recovery"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Denizen08 on 2007-12-28
[INDENT]I had a WinXP OS installed in my K8Combo-Z (Asrock) Desktop, on my Stripe Raided Sata Disks. Unfortunately my WinXP  got screwed by some virus. Now I cant boot into it. Im currently using ubuntu on a spare IDE Disk, and after testing it out I've decided to use it as my main OS. I'm gonna have to dual boot (for the usual reasons converts, like me, still need to use Windows), unfortunately I dont know how to go about reviving my Raid for Linux.[/INDENT]

I am going to renew the entire raid for my final setup, but I need to recover some data first. How do I go about to mounting my Raided disks without having to renew it first? I (think) am  using a Hardware-based Raid utility directly from my Motherboard which is a K8Combo-Z. Also I dont know what raid (chipset?) I am using... M5289?... I tried looking in AsRock for a linux Raid driver but they only have Windows drivers.:confused:

Thanks in advanced
Jay

---

### Post by blueridgedog on 2007-12-28
If you raid array is a hardware array and it is healthy, it should show up to Ubuntu as a normal "disk" (if Ubuntu recognizes your HWRaid chip).  Can you post the output of the following commands?

sudu fdisk -lu

mount

cat /proc/partitions

Also, other than the array, what disks do you have in the system and how are they setup to your knowledge?

---

### Post by Denizen08 on 2007-12-29
> **blueridgedog said:**
> Can you post the output of the following commands?

sudu fdisk -lu

mount

cat /proc/partitions

I'm not sure myself, but don't you need a target device (/dev/...) for those commands to work? In light of that, I found the disks that were supposed to be raided. The two are labeled "sda" and "sdb" and not as a raid array. I dont know how else to mount the raid without renewing it, it might be dead... but I'm hoping for the best.

> **blueridgedog said:**
> Also, other than the array, what disks do you have in the system and how are they setup to your knowledge?

I only have 3 disks... 2 sata both of which fits in my raid, and a IDE HD where my current OS is located.

Also, if I might ask what kind of raid do I actually have? I believe the mother board I use is capable of RAID but any OS I install still requires a driver (device controller?).

---

### Post by blueridgedog on 2007-12-30
You do not need a target, they are informative on their own and would help me and others to give you a hand.

Given that we don't have any output from those commands:

If we **assume** that they are sda and sdb and that there is only one partition on each of them and that single partition is supposed to be the array, and that neither of those partitions are mounted currently, then you can mount them in an array with the following.  However, it is unlikely that this will allow you to recover your files, so move forward as long as you understand that the advice I am giving you at this point is [B]destructive to the data on the disks:
[/B]
Install mdadm:

sudo apt-get install mdadm

Make a raid array (I put in raid 0 here as you mentioned you were striping for performance).

$ mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1

Restart the system, using the following or the GUI

$ shutdown -r now

This forces the disks to be synced, watch the process if you curious with cat /proc/mdstat

At this point if you think there can be a miracle, you can mount the new raid volume /dev/md0  (let me know of you need syntax on that, but it would be similar to what follows **omitting** the mkfs step, but I suspect you would use ntfs-3g as the system type) or you can assume that there is no chance of data recovery and format it:

$ mkfs -t ext3 /dev/md0

You can mount your new raid array with

sudo mkdir /mnt/MYRAID (or whatever you want to name it)

sudo chown USER:USER /mnt/MYRAID (use your user id)

mount -t ext3 /dev/md0 /mnt/MYRAID

You would need to put this entry in /etc/fstab to have it mounted automatically.

---

### Post by Denizen08 on 2007-12-30
Wow, thanks for the help here especially since its the holidays.:)

By the way, belated Merry Christmas and a Happy New Year. :KS

---

