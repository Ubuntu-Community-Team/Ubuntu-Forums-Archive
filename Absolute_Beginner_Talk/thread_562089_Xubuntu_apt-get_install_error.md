---
title: "Xubuntu apt-get install error"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by doanotherlinux on 2007-09-28
I had been running Xubuntu on my machine for a few days and the add/remove programs app froze on me.  I restarted.  And when the machine turned on it stopped and told me that apt-get is not installed.

So being as new to Linux as I am I tried to reinstall Xubuntu all over again.  Everything went good.  Except during install it stalled for a long time(probably 30 minutes or so) when the software install was around 85%.

When I started it after the fresh install I got the same apt-get not installed error.

Anybody know whats wrong?

And please dumb it down the best you can.  As I really have little to no idea what I'm doing.

---

### Post by FuturePilot on 2007-09-28
You need to fsck the drive. Easiest way to do this is to boot from the live CD and in a terminal do
```
sudo fsck /dev/sdaX
```
Where X is the drive partition. Such as /dev/sda1 or /dev/sda2 or whatever the partition in question is.

---

### Post by doanotherlinux on 2007-09-28
I should have pointed out.  I have the alternative disk.  So I don't know if I can do a live CD thing with it.

---

### Post by overdrank on 2007-09-28
> **doanotherlinux said:**
> I should have pointed out.  I have the alternative disk.  So I don't know if I can do a live CD thing with it.

Hi have you check the cd for errors? Have you verified the cd it could have been corrupted during download.  
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Also could you give us some specs on the system?

---

### Post by doanotherlinux on 2007-09-28
The disk is fine.  I already used it to install Xubuntu with no problems.  But now its giving me trouble.  I also checked the disk verify thing and it says its good.


The machine is a Compaq Presario 5000.  256mb of RAM.  40gb Hard drive.  1200(I think)mzh Processor.

---

### Post by doanotherlinux on 2007-09-28
bump.  Still ain't figured it out.

---

### Post by FuturePilot on 2007-09-29
Can you boot it into Recovery Mode? I'm almost positive all you need to do is fsck the drive. The only other way I know how to do this without a live CD is to do this
```
sudo touch /forcefsck
```
Then reboot
```
sudo shutdown now -r
```
That will cause an fsck on reboot. 
If you can get into recovery mode you might want to give this a shot.
Just make sure to delete the file fsck in the root file system (/) afterwards or else your computer will fsck on every boot.

---

