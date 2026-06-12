---
title: "Critical problem"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by MaestroS on 2006-11-17
I was installing Linux, and I didn't looked at partitions, and it deleted my Windows XP.

Now, when I want to install Windows, and I'm at step of choosing partitions to install Windows, it says that these partitions are unknown for him.


Here is my question:
How to remove Ubuntu from disk and back NTFS file system to get back Windows?

I don't want Ubuntu anymore - it destroyed my 2 year data downloading and keeping!

... and I want Windows back, and NTFS file system... too!

---

### Post by bodhi.zazen on 2006-11-17
If all you want is windows just let the windows CD format the entire disk.

If you would like to "play" with Liinux, download [Gparted](http://gparted.sourceforge.net/livecd.php) and make some partitions to play with....

---

### Post by MaestroS on 2006-11-17
You mean, format will delete Ext2 file system and place NTFS on Windows installing process?

---

### Post by bodhi.zazen on 2006-11-17
> **MaestroS said:**
> You mean, format will delete Ext2 file system and place NTFS on Windows installing process?

Yes.

---

### Post by tchoklat on 2006-11-17
yes WIndows will repartition the entire hard drive deleting everything on it. When it has done this it will install XP for you. You can then use [Gparted]("http://gparted.sourceforge.net/livecd.php") to play withit. Note that the live CD of Ubuntu will create a new Ext2 file partition for itself and not affect windows XP when you install it so you can dual boot to either XP or Linux!
 
Tony

---

### Post by biffta on 2006-11-17
MaestroS, where are you with this now?
> I don't want Ubuntu anymore - it destroyed my 2 year data downloading and keeping!

I hate to be the one to tell you, but Ubuntu only did what you told it to. I would hazard a guess that your old data "might" still be around. You have to be pretty explicit in order for Ubuntu to delete something at the install stage. It may just be that your old data is on a partition which you have been unable to re-mount.

If it was me, I would download a live linux CD like [Knoppix]("http://www.knoppix.org/"). Usually when you boot up a disk like this, it will mount everything it can, so you might be surprised to see all you old data is still there. It's only a "might" thought!

---

### Post by MaestroS on 2006-11-17
They're wont be there anymore, cause on disk D: is now Ext2 file system, and when I would change it into NTFS, Windows should format this partition, and all data I collected and is necessary , will be lost ... So, this data recovery is not possible anymore... I mean, I think that. Maybe someone can tell me... or... im gonna cry... 20gb of data... changed into Ext2... and now it will be lost when change to NTFS... let me die...

---

### Post by Amolad on 2006-11-17
you CAN have two filesystems on the dame disc you know.... separated by partitioning. in order for linux to see the windows partition you have to mount it. unless you told it to mount automatically during the install phase (this is not done by default) then you will have to do it manually.

im not sure exaxtly on how this is done but googling for something like 'mounting a windows partition in ubuntu' or something along those lines should get you what you are looking for.

are the OSes on different hard drives or different partitions of the same one?


EDIT: since you quoted D: drive there i think they might be, in which case change the primary drive in your BIOS settings back to your C: drive and it should boot into windows instead.

EDIT2: since i have nothing better to do i have researched abit.

 How to mount/unmount Windows partitions (NTFS) manually, and allow all users to read only

    Assumed that /dev/hda1 is the location of Windows partition (NTFS) 
    NOTE: hd** refers to the drive and partition. for example drive 'a' partition 2 would be hda2
    Local mount folder: /media/windows 

    * To mount Windows partition 

$ sudo mkdir /media/windows
$ sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

NOTE2: if it is a fat32 drive use this command instead.
$ sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

    * To unmount Windows partition 

$ sudo umount /media/windows/


(the $ means for you to enter it in the terminal (minus the $))

---

