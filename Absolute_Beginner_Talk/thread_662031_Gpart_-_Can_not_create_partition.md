---
title: "Gpart - Can not create partition"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Jacoo on 2008-01-08
The problem is not that when I try to run gparted live cd and gparted from the ubuntu live cd it can not make any partitions.

When I start gparted live cd I choose the first option "Gparted-live cd 0.3.4-11 (auto-config) I have never used the program before so I would not start to guess around. Just before the keymap it looks like Gparted is running a check:

>>attempting to mount media:- /dev/sda
>>attempting to mount media:- /dev/sda1
>>attempting to mount media:- /dev/hda
>>media found on /dev/hda

I choose keymap and language.

After a while Gparted stops and I have to write: 
Forcevideo 
Vesa

After that Gparted runs just fine until I need to create a swap disk then it goes wrong. 

My whole hard disk /dev/sda is unallocated space.

When I set it to make a Linux &#8211; Swap at 4 GB at /dev/sda1 (I heard somewhere it should be twice my ram (2bg)) partition Gparted stops after a while and says:

&#8220;mkswap /dev/sda1: no such file or directory&#8221;

Its the same deal on ext2 and ext3. Do i even have a Sda when Gparted finde the media on hda?

I really hope for some help ?

Cheers 
Rasmus

---

### Post by chuckyp on 2008-01-08
Try typing in fdisk -l to list the partitions that you curently have.  Also I'm not sure how you are trying to create a swap first?  It shouldn't be made like that it should be an extended partition.

---

### Post by timbounceback on 2008-01-08
> **chuckyp said:**
> Try typing in fdisk -l to list the partitions that you curently have.  Also I'm not sure how you are trying to create a swap first?  It shouldn't be made like that it should be an extended partition.

You  may want to make that ```
sudo fdisk -l
```:)

---

### Post by L Campbell on 2008-01-08
> **Jacoo said:**
> The problem is not that when I try to run gparted live cd and gparted from the ubuntu live cd it can not make any partitions.

When I start gparted live cd I choose the first option "Gparted-live cd 0.3.4-11 (auto-config) I have never used the program before so I would not start to guess around. Just before the keymap it looks like Gparted is running a check:

>>attempting to mount media:- /dev/sda
>>attempting to mount media:- /dev/sda1
>>attempting to mount media:- /dev/hda
>>media found on /dev/hda

I choose keymap and language.

After a while Gparted stops and I have to write: 
Forcevideo 
Vesa

After that Gparted runs just fine until I need to create a swap disk then it goes wrong. 

My whole hard disk /dev/sda is unallocated space.

When I set it to make a Linux – Swap at 4 GB at /dev/sda1 (I heard somewhere it should be twice my ram (2bg)) partition Gparted stops after a while and says:

“mkswap /dev/sda1: no such file or directory”

Its the same deal on ext2 and ext3. Do i even have a Sda when Gparted finde the media on hda?

I really hope for some help ?

Cheers 
Rasmus

I had trouble recently, trying to make partitions in a pen drive.

Someone suggested that I should first remove the existing partitions.

This seemed to work well for me.

---

### Post by Jacoo on 2008-01-09
> **timbounceback said:**
> You  may want to make that ```
sudo fdisk -l
```:)

in the terminal on the ubuntu live cd?

When i start Gparted there are no partitions only unallocated space.

Thanks a lot for the fast replys :)

---

### Post by Jacoo on 2008-01-09
When i boot the ubuntu live cd and types ```
sudo fdisk -l
``` in the terminal it says:

Disk /dev/sda: 200.0 Gb, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = Cylinders of 16065 * 512 = 8225280 bytes

Device boot             Start                 End              Blocks         id                    system
/dev/sda1                 1                       510          4096543+    82             Linux swap / Solaris

---

### Post by Jacoo on 2008-01-09
I am able to make a extended partition now but not a ext3 or a swap partition.

Am i doing something totally wrong?

---

