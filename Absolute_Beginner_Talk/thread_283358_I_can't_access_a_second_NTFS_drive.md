---
title: "I can't access a second NTFS drive"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by oliverb on 2006-10-24
So I got this call that a PC wouldn't start and it had important files on. I took out the hard drive and connected it to a different machine. I tried Ubuntu first as I find XP tends to hang if you attach a dodgy drive. Anyway I cannot access the second drive, I tried the drives configuration screen and tried to mount it at media/windows2 but I either got odd file permissions errors or that the partition was unreadable.

I gave up and used Windows, the drive turned out to be OK and the unbootable PC turned out to have a floppy disk in.

I've had this before, last time I was using a drive connected via a USB2IDE bridge and I'd tried "cloning" the main drive using DD but again the NTFS part of the external drive was unreadable.

Anyone know what's going on?

---

### Post by tommy18crowe on 2006-10-24
Yeah Ubuntu won't show NTFS partitions because they need to be mounted, and in order to mount them you need to be root.

Commander

---

### Post by oliverb on 2006-10-24
I don't know, I think it's more complex than that as I followed the instructions before and got my normal windows partition visible, it's visible under media/windows. 

Also when I tried the configuration tool I was asked for my password so it was running as root at the time.

Also all other USB drives seem to auto-mount OK.

---

### Post by Epperly on 2006-10-24
I used to have this problem too..
this was my solution:
[http://www.ubuntuforums.org/showthread.php?t=142481&highlight=access+windows+files](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=access+windows+files)

---

### Post by bulldog on 2006-10-24
When partitions are listed in fstab you'll see them in /media.

If you atach a 'strange' hdd ,which is not listed in fstab,you have to mount manually.

To do so you have to create a mountpoint like,```
sudo mkdir /mnt/strange-disk
```

Then you have to mount the partition you want to see,you can find the right one with```
sudo fdisk -l
``` l as in like.

Mounting is done like this```
sudo mount -t ntfs /dev/hda? /mnt/strange-disk
```

---

