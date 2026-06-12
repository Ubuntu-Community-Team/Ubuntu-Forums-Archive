---
title: "Ready to ditch windows, need help with partitioning."
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jonnywombat on 2007-04-30
Hello 

After much playing and tinkering I am now ready to make my laptop ubuntu only, and I am ready to ditch windows completely.

This started off life as a machine running xp, on two partitions one for the operating system and one for data (c: and d: )

when I installed ubuntu I moved the data from d: to c: and then re wrote that partition as my ubuntu partition.

So now my HDD looks like this..
 
/dev/hda1 is linux swap

/dev/hda2 is nfts  (windows) with mount point of "/media/hda2" and is flagged as boot.

/dev/hda3 is ext3 (ubuntu) mount point "/" no flag
In gparted all partitions are shown as "locked" 


How do i go about removing the windows partition without destroying or reinstalling ubuntu, and hence losing my data and customizations.


Thanks in advance

Jonny

---

### Post by Spike-X on 2007-04-30
I imagine all you'd have to do is fire up Gparted and delete dev/hda2.

---

### Post by adewale on 2007-04-30
have u tried unmounting d drive try sudo umount -a then try re partitioning again

---

### Post by jonnywombat on 2007-04-30
> **Spike-X said:**
> I imagine all you'd have to do is fire up Gparted and delete dev/hda2.

Thats what i thought, but when I try to do that the relevant options are greyed out, and cannot be selected. In the descriptions of each partition there is a icon of a locked padlock, I guess I need to find a way of "unlocking" them but I do not know how.

Jonny

---

### Post by jonnywombat on 2007-04-30
> **adewale said:**
> have u tried unmounting d drive try sudo umount -a then try re partitioning again


Thanks for the idea..

Terminal gave this 

-laptop:~$ sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy


No joy

Jonny

---

### Post by Spike-X on 2007-04-30
Ah yes, I forgot about the padlock bit. Hmm...

---

### Post by jonnywombat on 2007-04-30
> **jonnywombat said:**
> Thanks for the idea..

Terminal gave this 

-laptop:~$ sudo umount -a
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy


No joy

Jonny

I jumped the gun in saying no joy,

After running this I fired up gparted and the padlock was gone and I was able to delete the ntfs partition making it unallocated space. However I cannot add this space to the existing ubuntu partition as that is still locked.

Thanks for help so far... Getting there slowly

Jonny

---

### Post by adewale on 2007-04-30
okay that should have worked in gparted i think there's an option when you right click on a partition it allows you to unmount it

---

### Post by jonnywombat on 2007-04-30
Thankyou 

So I now have 14 gb of unallocated space. 

Can I just add this to my main linux partition(28gb) or is there a way of making better use of this space? And if so how do I configure it?

Jonny

---

### Post by Spike-X on 2007-04-30
A suggestion; this is something I do with all my computers (not that I've had many), and any computer I set up -

Make yourself a separate storage partition. That way, if something gets hosed and you need to wipe your Ubuntu partition and do a fresh reinstall*, you'll still have all your data files (music, pics, videos, documents, etc).

I suppose having your /home directory on a separate partition could also provide that level of safety - perhaps a more experienced user could advise you if there's a way to migrate your existing /home directory to a separate partition?



*I don't know what the odds are of this actually happening, but as any Windows user knows it's a very real possibility under that OS, and I've just gotten into the habit.

---

### Post by jonnywombat on 2007-04-30
[SIZE="6"]Well that's completely borked my laptop....lol[/SIZE]

[SIZE="2"]I shut my laptop down for a few moments and now it will not reboot!!. If you are trying to achieve what I was then don't use this method.. As I forgot that it would delete my mbr too!!! D'OH.


Well I guess it's back to the live cd, just what I wanted to aviod, unless anyone knows how to fix this.


 [/SIZE]

---

### Post by vanadium on 2007-04-30
My understanding is that you currently have a dual boot system, with one linux system partition, probably a linux swap partition and two ntfs partitions, one where your XP boots and one that you use for data. If you want to go completely to Ubuntu, then you probably want all partitions formated in ext3. What I would have done in your scenario is:

* move my data to an USB drive
* delete both NTFS partitions
* create one new data partition formatted with the ext3 file system

Possibly, you will need to move partitions if the two NTFS partitions are not on a contiguous space of the disk. Moving existing partitions without data loss will require the use of GParted, and there, you are better off using a life CD.

Yet by far the easiest approach will be to reinstall Ubuntu from scratch.

---

