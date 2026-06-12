---
title: "How do I mount fat32 40G external drive?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by neatokino on 2008-02-24
This question has been asked many many times, and I've read through as many previous posts as I can, but I'm still clueless here:

I have a 40G external firewire drive that I formatted using gparted as fat32.  I want to use this drive to move files from one computer running Gutsy to another running Gutsy AND to my Macbook Pro.  The external drive mounts fine on the Macbook Pro, and I can drag files on to it.

I cannot, however, figure out how to mount the drive on my Gutsy computers.  If I type sudo fdisk -l, I get:

> Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024893

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2           89723       91201    11880067+   5  Extended
/dev/sda3            2551       89722   700209090   83  Linux
/dev/sda5           89723       91201    11880036   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000183e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   b  W95 FAT32


So, the hard drive is /dev/sdb1, and it is recognized  by Gutsy as being plugged in, but it doesn't show up on the desktop nor on nautilus, nor can I figure out how to mount it.

What do I do to mount the drive and to make it mount automatically every time I hotplug it in?  

Also, do I have to do anything to make it readable and writable on all three of my computers?  

TIA
Michael

---

### Post by Ardrias on 2008-02-24
Can you mount it manually by entering ```
sudo mount /dev/sdb1 /home/SomeUser/SomeDirectory
``` ?

---

### Post by neatokino on 2008-02-24
When I try sudo mount /dev/sbd1 /home/michael/Desktop  I get:
> 
mount: special device /dev/sbd1 does not exist

---

### Post by oedha on 2008-02-24
> **neatokino said:**
> When I try sudo mount /dev/sbd1 /home/michael/Desktop  I get:
suppose to type sdb1
:)

---

### Post by dcstar on 2008-02-24
> **neatokino said:**
> This question has been asked many many times, and I've read through as many previous posts as I can, but I'm still clueless here:
.............
What do I do to mount the drive and to make it mount automatically every time I hotplug it in?  

Also, do I have to do anything to make it readable and writable on all three of my computers?  

TIA
Michael

Since this is an **external** drive, it will mount automatically if you have the "Mount" options enabled in System-Preferences-Removable Drives and Media.

FAT32 does not really have any way of preventing R/W access at a user level, the default Ubuntu mount should be R/W.

If you want the partition mounted at a consistent location, label the partition and it will be always mounted with that name.

---

### Post by neatokino on 2008-02-24
Thank you for noticing the typo-- I'm an idiot!  

So, yes, I mounted the drive to 'Desktop' and it DOES show up, which is good, but it looks like it obliterated everything that was on my Desktop before. 

How do I unmount it from the Desktop and create another directory to mount it to??!!??  And, once I figure that out, is there a way to make the drive automatically mount to that directory when I plug it in???

Thanks again

BTW, I DO have the Mount options set to automatically mount in System-Preferences-Removable Drives and Media, but that doesn't seem to get it mounted.

---

### Post by oedha on 2008-02-24
sudo umount /your_temporary_mouonting_point
then
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
since it is FAT32....i think...will ccaused you no problem.....

PS : you're not an idiot....just misstypo...:)

---

### Post by neatokino on 2008-02-24
thanks again...

unfortunately, when I do the 'umount' command, it doesn't unmount the disk and bring back my old desktop:

> ~$ sudo umount /home/michael/Desktop
umount: /home/michael/Desktop: not mounted


did I obliterate everything that used to be my desktop permanently??  I'm afraid to just unplug the drive now.

---

### Post by oedha on 2008-02-24
wait.....
it suppose to be :==> sudo umount /home/michael/Desktop/[B]something_else

[/B]

---

### Post by neatokino on 2008-02-24
unfortunately, there is no 'something else'!  I just mounted the external drive to /home/michael/Desktop.    I realize now that was a mistake, that I should have made a new directory on the Desktop, but that's not what I did.    How do I undo this and get my old desktop back?

---

### Post by oedha on 2008-02-24
waaaa.......you mean that all things on your desktop ?
i have no experience about that....sorry
let see.....
what if sudo umount -a
did they gone ?

---

### Post by neatokino on 2008-02-24
I got them to go away by restarting the computer and unplugging the drive... everything is fine.  Now, I DID get the drive to mount to /media/sdb1, which is a step in the right direction.  Is there a way to get it to mount that way automatically when I plug it in?

Oh, and thanks again. You are being very helpful and it is much appreciated!

---

### Post by oedha on 2008-02-24
hahahaha...........finally
for your next question...maybe you have to read post #5.......by dcstar

you're welcome !!

---

### Post by neatokino on 2008-02-24
thanks again.  Yes, I read dcstar's post and did as he said, but the drive still does not mount automatically.  Ah well... I suppose I'll have to just mount the drive with terminal commands whenever I want to use it (which is no fun at all).

I must say that it would certainly help Ubuntu's acceptance as an easy-to-use alternative to Windows and Mac if there were easier ways to deal with hard drives!    I love using Ubuntu, but issues like this can be extremely frustrating in comparison to Mac's consistently good 'plug and play.'

---

### Post by oedha on 2008-02-24
you did mark on those 2 mount ?
and not automatically yet ?
mmm....it worked on me ! just like flashdisk

---

### Post by neatokino on 2008-02-24
No, it won't mount automatically (if it did, I would never have posted here in the forum... I had those mounting options checked all along).  If anyone has any  solutions, please send them my way!

---

