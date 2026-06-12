---
title: "Disk Space Problem!"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by matteospqr on 2007-06-02
Hello!!

I am totally new to linux and I just installed Ubuntu a few days a go.  Everything went smoothly until today...I probably downloaded a few extra things and the 5GB I gave the linux partition are now practically full.  
When I try to log in it wont let me saying the disk is full and he is unable to write the login.
I got in using the LIVECD but after opening the partition program I was unable to give HDA-1 more space.  
What I was able to do was to take 5GB from the Windows partition but I dont know how to merge these 5GB of unallocated space with the HDA-1 (ubuntu partition).

HELP!!!! :)

---

### Post by taurus on 2007-06-02
Boot into recovery mode from GRUB menu and run

```
aptitude clean
```
That would buy you some space so you can log in again.

```
shutdown -r now
```
Don't forget to remove stuff that you don't need and also empty your trash bin too.

And if you want to merge it, use GParted LiveCD since it comes with the latest version of gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by matteospqr on 2007-06-02
Thanks! But how will I manage to merge the 5GB that I got from windows with the UBUNTU partition??

---

### Post by ugm6hr on 2007-06-03
> **matteospqr said:**
> Thanks! But how will I manage to merge the 5GB that I got from windows with the UBUNTU partition??

In GParted - right-click on the Ubuntu partition and select Resize/Move.  Then just click on the up-arrow next to partition size until it won't let you make it any bigger.

PS: This is only possible if the "unallocated" space you retrieved from Windows is next to the Ubuntu partition.  If Ubuntu is an "extended" partition (e.g. hda5-8 ) - you will have to resize the full extended partition first.  If this doesn't work, or doesn't make sense, just post a screenshot of GParted.

---

### Post by hyper_ch on 2007-06-03
Before you change the sizes of the partitions... make backups from the important data on that disk (not only of the affected partitions). There is a small chance that resizing may render the disk unusable...

---

