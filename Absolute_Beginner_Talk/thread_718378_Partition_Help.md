---
title: "Partition Help"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by DarkSaga70 on 2008-03-08
I am pleased to say that after many years of windows slavery I am finaly breaking the chains. Now I dual boot and am ready to do away with that forever and want to dump my windows partition and add it to my linux partition, How do I do this?

---

### Post by NightwishFan on 2008-03-08
Sorry let me edit my post. I misread. Boot up the Ubuntu live cd, and use gparted to merge them. Remember to hit "apply".

---

### Post by DarkSaga70 on 2008-03-08
I have it installed already. Is there a way to partition it from within linux? normaly I would use admin tools in windows but can not seem to find anything like that in 7.10?

---

### Post by NightwishFan on 2008-03-08
Edited my previous post.

---

### Post by DarkSaga70 on 2008-03-08
Maybe I was not clear...I have already both OS's installed but I want to dump Windows and keep Linux. I can not figure out from within Linux how to do this. Is it possible or am I stuck totaly reformatting?

---

### Post by DarkSaga70 on 2008-03-08
Ahh thanks :D

---

### Post by ahaslam on 2008-03-08
No need to reinstall, simply use Gparted, Unless you have another distro on a separate disk, you'll require the live cd. It'll allow you to delete, move & resize your existing partitions & create new ones. If you're using the default ext3 filesystem, this'll be safe & straightforward.

;)

---

### Post by NightwishFan on 2008-03-08
Maybe I was not clear. I do not mean reinstall. Use gparted in the live cd. I am unsure if you can merge them or not while Ubuntu is mounted. If you want to try it right now.

sudo apt-get install gparted

---

### Post by forestpixie on 2008-03-08
I assume that the windows partition you want rid of is at the front of the drive

sudo fdisk -l

will help with that

1 - you could use gparted to do this - it will let you delete the windows partition and move it so that is to the right of the buntu one - once there you can extend the buntu partition to take up the spare.

when you reboot - use the live cd first so that you can edit the fstab in order to mount the disc again

2 - use gparted to format the partition to ext3 or whatever you want to use, then you can add the partition to the setup as a seperate data partition

---

### Post by DarkSaga70 on 2008-03-08
I dont suppose you could walk me through that could you I can not seem to find it on the cd and it wont let me launch executibles as well?

---

### Post by forestpixie on 2008-03-08
you won't be able to do anything to the existing linux install while the partitions are mounted - do it with either the gutsy livecd which has gparted or get a gparted livecd - make sure you have suitable backups of anything you can't afford to lose

---

### Post by forestpixie on 2008-03-08
You might be able to do it from within linux - in system >admin > part editor
if you can right click unmount the windows partition you will be able to do it without either livecd, if not boot to the livecd

before you do anything post the output of ```
sudo fdisk -l
```
use gparted to delete the win partition, create a new partition

then we can edit fstab to add the new drive and lose the old win one, post the following

```
cat /etc/fstab
blkid
ls media
```

---

