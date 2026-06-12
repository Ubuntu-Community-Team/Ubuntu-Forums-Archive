---
title: "Mounting Hardware?"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by zachattackzero on 2006-12-27
I just installed Ubuntu because my XP became corrupted and wouldn't boot up, blah blah blah...  Now I can't figure out how to be able to access my secondary hard drive that is my media hard drive and stuff.  I also just realized that my sound card isn't working with it and doubt that my floppy drive or DVR-RW drives work...  Will someone please explain to me how to "mount" my hardware so that I can use the stupid stuff?  PLEASE!?

---

### Post by cotcot on 2006-12-27
It is strange that you do not have your other disk mounted. Need more info to check why. Check your /etc/fstab and see if you have an directory for each device you have. 
Search for the partition on your second disk you want to mount with :
```
sudo fdisk -l
```
This will show your drives and partitions.
Then 
```
sudo mkdir /mnt/anynameyouwant
mount /dev/hda1 /mnt/anynameyouwant
```
hda1 to be replaced with the name of the partition on your second disk you want to mount

---

### Post by houstonbofh on 2006-12-27
> **zachattackzero said:**
> I just installed Ubuntu because my XP became corrupted and wouldn't boot up, blah blah blah...  Now I can't figure out how to be able to access my secondary hard drive that is my media hard drive and stuff.  I also just realized that my sound card isn't working with it and doubt that my floppy drive or DVR-RW drives work...  Will someone please explain to me how to "mount" my hardware so that I can use the stupid stuff?  PLEASE!?
Too many problems that are probably unrelated.  Lets break it down a bit...

Secondary hard drive access...  What is it NTFS?  Fat32?  If you want full R/W to NTFS look at [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Sound card...  What kind?

Floppy and DVD-R/W...  Why do you feel that these do not work?  Have you put anything in the to test?

How to mount...  Most stuff automounts.  (USB drives, CDs...)  However, that requires media detection, which a lot of floppy drives just don't have.  There are some tabs in nautilus that may help you here.

---

