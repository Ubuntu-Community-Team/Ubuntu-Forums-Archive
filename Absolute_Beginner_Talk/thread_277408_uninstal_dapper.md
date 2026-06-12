---
title: "uninstal dapper"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by bilbobagins on 2006-10-14
Can someone let me know the easyest way to uninstal dapper, so i can the reinstal and hopefully cure the vidio output to my monitor ( shifted to right) as i cant fix the problem so clean instal should cure this. thanks

---

### Post by taurus on 2006-10-14
Before reinstall it, run this command to reconfigure your X from a terminal to see if it fixes the problem!

```
sudo dpkg-reconfigure xserver-xorg
```
Otherwise, just format the partitions during the installing process and it will wipe out the old version and install the new version on your machine.

---

### Post by K.Mandla on 2006-10-14
If you really, really want to start over with a clean slate, you could run [Killdisk]("http://www.killdisk.com") first. It will take a while depending on the size of the drive, but the entire space will be written over with zeros. It's the next best thing to a brand new hard drive.

---

### Post by bilbobagins on 2006-10-15
Thanks for replies,I will try these tomorrow as im at work now till 5am monday........ Life sucks sometimes!:rolleyes:

---

### Post by taurus on 2006-10-15
> **bilbobagins said:**
> Thanks for replies,I will try these tomorrow as im at work now till 5am monday........ Life sucks sometimes!:rolleyes:

Hey, we all have to work since the bills need to be paid unless you have a rich parents.  Then, you don't have to work and you get all the expensive toys to play with!!!

---

