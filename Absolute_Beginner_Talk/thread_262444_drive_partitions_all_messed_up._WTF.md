---
title: "drive partitions all messed up. WTF?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ironslave on 2006-09-21
ok i previously decided to delete my 2 windows partitions and make my PC a full ubuntu system....... but heres the issue.... i made a new ext 3 partition on the drive space (the windows partition was before the ubuntu partition) and was just gonna copy the files over and resetup a boot manager... well the new extention is reading as the swap drive (1st partition) and the swap drive is reading as an NTFS. than there a mystery NTFS sitting on my drive allong with 6 gig's of empty space... this is all in the drive manager under the administration menu.... but under qtparted and gparted it all read as it's supposed to.... anyone know whats going on?

---

### Post by aysiu on 2006-09-21
I have no idea what's going on, but I would trust the output of ```
sudo fdisk -l
``` over both the drive manager and GParted.

---

### Post by ironslave on 2006-09-22
yea the fdisk command produces the same as i had partitioned the system to..... is there a reason that the 2 NTFS partitions on my drive still show up even though i deleted them?

---

### Post by b_martinez on 2006-09-22
Have you  re-booted the system after making the changes? You sometimes need tto do this for the changes to take effect.
Bill

---

### Post by encompass on 2006-09-22
Please copy and paste that output from that command... that we will all can know exactly what is going on.

---

### Post by ironslave on 2006-09-22
ive restared.... run g parted on it. qt parted and all off of live CD.

heres the information outut from fdisk

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         392     3148708+  82  Linux swap / Solaris
/dev/hda2            5100        6438    10755517+  83  Linux
/dev/hda3             393        5099    37808977+  83  Linux

Partition table entries are not in disk order

---

### Post by encompass on 2006-09-22
looks like two linux parttitions and a swap to me.
Are you ready to install?
Is this the way you wanted it?=
list each a parttition and it's size that you want in your next post.
by organized and lay it out like this...
drive  type size  location
hda1   EXT3 10GB  /
hda2   SWAP 1GB   swap
hda3   EXT3 249GB /home/

---

### Post by ironslave on 2006-09-23
ok i figured out the issue.. fstab was sill loading the ntfs partitions...

so heres the new issue.... what do i do to make the drives mount on live CD to copy all the files over... 

but i sill cant mount the 34GB to my system :( i tried mounting it with fstab and it gives me some reason about it being unmountable.... so what do i do? the disk manager wont do anything either. e.g. what do i need to put in fstab to make the drive usable

i WOULD like to combine the 36gb of empty space and the current filesystem  all into one drive and than keep my current swap and make the 6 gb into my music partition

hda1 SWAP 3GB SWAP
hda2 ext3 45GB /
hda3 ext3 6GB /music/

---

### Post by encompass on 2006-09-24
So...
You want to mount your ntfs partition while running the livecd?

You want to create a partition set like you have listed?
I would recommend putting th swap in the middle. ( it is my experience that you should have your /boot and / at the front of your drive.  Why do you need so much swap?   A GB should be just fine for most people.  I run on 512mb of swap.

If you are not worried about loosing data... swipe the drive by simply using the install program.  Somtimes the screen that shows the partitions goes grey... jsut click on it to get your images of the partitions back.

Show your questions in plain view... I can't seem to get what your trying to say.

---

