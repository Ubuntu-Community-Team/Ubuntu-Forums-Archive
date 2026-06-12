---
title: "Mounting Linux Partition with LIVECD"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by aminahmadi on 2006-08-20
So here is my ordeal... 
I had an Ubunu on a computer.... and bunch of files I am trying to save. I can't boot from that installation anymore. 

The hardrive has Linux partition, a linux swap and an NTFS partition. 

I got another machine with Windows XP and I tried programmes like explore2fs but couldn't access the files on that.

I figured I could use LIVECD to boot up on any machine and then dump the files from the HDD to a USB key and be done with it. But I am too much of a Windowsicated person to pull a stunt like that. 


How could I mount this drive

---

### Post by aysiu on 2006-08-20
If you have a Knoppix CD (which is built for recovery purposes), you can just click on the drive, and it'll mount with the correct permissions.

If you have a Ubuntu live CD (which is *not* built for recovery purposes), you would do ```
sudo fdisk -l
``` to find out where your Ubuntu partition is. Let's just say it's */dev/hda2* for now. ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda2 /recovery
gksudo nautilus
``` Then press Control-L and type ```
/recovery
```

---

