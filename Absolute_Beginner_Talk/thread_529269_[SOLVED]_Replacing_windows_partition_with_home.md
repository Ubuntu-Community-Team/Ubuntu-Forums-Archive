---
title: "[SOLVED] Replacing windows partition with /home"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by therandman on 2007-08-19
Does someone know of a quick way to remove a windows xp partition and immediately replace it with a /home partition?

---

### Post by logos34 on 2007-08-19
yep.  unmount the windows partition.  Open Gparted (Gnome partition editor) and format it ext3.  Delete the windows entry in /etc/fstab.  Then transfer your /home/user directory using [this guide]("http://www.psychocats.net/ubuntu/separatehome").

---

### Post by therandman on 2007-08-19
I will give it a try, thanks!

---

### Post by therandman on 2007-08-20
> **logos34 said:**
> yep.  unmount the windows partition.  Open Gparted (Gnome partition editor) and format it ext3.  Delete the windows entry in /etc/fstab.  Then transfer your /home/user directory using [this guide]("http://www.psychocats.net/ubuntu/separatehome").

Question, how do I unmount the windows partition?

Actually, I did

```
sudo umount /dev/sda1
``` 

and it told me that it was not mounted.  Guess it would be safe to proceed and run gparted and format it?

---

### Post by Hobo Joe on 2007-08-20
> **therandman said:**
> Question, how do I unmount the windows partition?

Do the partitioning from the live CD.

---

### Post by therandman on 2007-08-20
Okay, everything seems to have gone as planned.  How do I find out if my /home is *really* on a seperate partition?

---

### Post by therandman on 2007-08-24
Re-questioning...how do I verify that /home is really on a separate partition?  

Also, I am getting ready to overwrite my Kubuntu with a fresh install, if I go with the default partitions, my /home will be safe, correct?  Then I will just have to edit the fstab to mount to the new /home?

---

### Post by bernied on 2007-08-24
The command 
```
mount
```
will tell you what is mounted where.
There should be a line that is something like '/dev/sda1 /home ...blahblah'

---

### Post by bernied on 2007-08-24
To answer your second question, your new /home partition should be safe, so long as you don't mess with it during the install. Adding it to the /etc/fstab may have strange consequences, depending on what versions of applications you were running and whether they are different from those installed in the new operating system.

---

### Post by therandman on 2007-08-24
Thanks for the answers!

But adding to entry to fstab is the only way right?  Or is there another way?

I will be replacing it with a fresh install and should be using all the same apps.  I've been doing a lot of playing with Kubuntu lately, and one of the consequences is no auto-mount for my external USB drives (well actually, they don't even show up anywhere).

---

### Post by bernied on 2007-08-24
> **therandman said:**
> But adding to entry to fstab is the only way right?  Or is there another way?

I will be replacing it with a fresh install and should be using all the same apps.  I've been doing a lot of playing with Kubuntu lately, and one of the consequences is no auto-mount for my external USB drives (well actually, they don't even show up anywhere).
There are other ways (like creating a tar archive), but since you've already done the hard bit, I think this will work best for you. If you are in any doubt, make a copy of the files somewhere else as well - like a cd or dvd.

---

### Post by therandman on 2007-08-24
> **bernied said:**
> There are other ways (like creating a tar archive), but since you've already done the hard bit, I think this will work best for you. If you are in any doubt, make a copy of the files somewhere else as well - like a cd or dvd.

Thanks bernied!

---

