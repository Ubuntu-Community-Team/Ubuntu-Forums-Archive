---
title: "why cant i resize my primary partition in gnome partition editor"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by robbie carrobie on 2007-05-08
when i run the live cd and try to resize my primary partition through Gnome partition editor, i get an error has occured, and the partition cannot be resized ,why is this? is it because there are some little padlocks besides my partition, do i need to unmount the primary partition that i am trying to resize, please help

---

### Post by icechen1 on 2007-05-08
> **robbie carrobie said:**
> when i run the live cd and try to resize my primary partition through Gnome partition editor, i get an error has occured, and the partition cannot be resized ,why is this? is it because there are some little padlocks besides my partition, do i need to unmount the primary partition that i am trying to resize, please help

You need to unmount any partition you want to change

---

### Post by robbie carrobie on 2007-05-08
thanks dude, i will try this and get back to you - regards robert.

---

### Post by robbie carrobie on 2007-05-08
dude this did not work either, i got little prompt after i clicked apply, which stated that an error had occurred, and a little stop sign, even though i could see the unallocated new space in my partitions listing - any ideas?

---

### Post by cypherzero on 2007-05-08
Try using a Live CD to partition, that way you can be sure the drive isn't being used.

When installing Ubuntu I ran across a problem where  gparted kept remounting my partitions after each opperation.
To work around this I had to do one opperation at a time and unmount after each, ie.
> Resize partition A.
> Apply
> Unmount A
> Create B
> Apply
> Unmount A and B
> Format B
> Apply
> Unmount A and B
> and on and on and on!

---

### Post by robbie carrobie on 2007-05-08
dude i was reading some stuff and have found out that it needs to be from a live cd cause you cannot resize or unmount a partiton that is in use, i will try your method and see if it helps, kind regards robert.

---

### Post by pgmer6809 on 2007-10-24
RESIZING ROOT PARTITION
I have just this minute completed doing this.
You can do it, provided that the partition is not mounted.
Since the root partition (/) is mounted by default, and so far as I know cannot really be unmounted, you have to do this resize from a live CD.
Put in the Live CD you used as an install CD (or DVD). and reboot.
When it starts go to system->Administration->Partition editor and start that.
Also go to Applications->Accessories->terminal and start that.
Be sure to close any windows Ubuntu opens for you that show you the contents of your hard drive.
Go to the terminal window and type in the cmd
```
sudo su
```
This will change your prompt to # showing you are now the root user.
Type the cmd 
```
mount
```
this will list all the mount points for you. 
Make a note of the device id for the partition you want to resize. it will probably be /dev/hda1 for an IDE device or /dev/sda1 for a scsi device.
type the cmd
```
umount /dev/hda1
```

Now you can go to the Partition Editor window.
Select the partition. If it has been properly unmounted the 'resize/move' button will be live and not greyed out. Click it.
Setup the new size of your partition. I shrunk mine so I could give more swap space.
Once you have done that you need to 'Apply' your new changes. gparted, is safety concious and gives you lots of warnings about backing up your data etc.
Do that.
After it is done, Ubuntu will remount the /dev/hda1 partiotion of its own accord.
Repeat the previous steps. I.e. Close the window UBUNTU opens for you, umount, etc.

Now you should be able to create a new partition.

If you want to delete the swap partition (because you want to make a bigger one e.g.) in the gparted application you can select the partition, then under the Partition menu item you can select 
```
swapoff
```
This will then let you delete the swap partition, and create a new one using the extra space from the first part, and the newlly freed up deleted swap partition.

Ubuntu will try to remount the /dev/hda1 partition after every step; just to be on the safe side I closed the window and umounted it every time, even when working on the swap partition.

Good luck.
pgmer6809

---

