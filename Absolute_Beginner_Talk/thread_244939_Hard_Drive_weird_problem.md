---
title: "Hard Drive weird problem"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by marko_4454 on 2006-08-27
I recently wanted to upgrade my 75GB PATA HDD to a bigger 250GB SATA HDD but I didnt want to lose my info so I just "copied" (using Ghost for Linux) from my 75GB to my 250GB Drive.

But today I ran into a problem: Ubuntu detects that my 250GB Drive is only 75GB big!!! 

Some more concrete info:

I can go to the Disks Manager and in the left side it detects my drive as a 250GB one, but in the when I select it. To the right, in the partition slot, it says that its only 75GB long.

I do not want to format it thats why I used G4L in the first place, but I dont know if formatting may be the only answer.Has anyone had this problem before? And what did you do?
-Thanks,
marko

---

### Post by Pragmatist on 2006-08-27
> **marko_4454 said:**
> I recently wanted to upgrade my 75GB PATA HDD to a bigger 250GB SATA HDD but I didnt want to lose my info so I just "copied" (using Ghost for Linux) from my 75GB to my 250GB Drive.

But today I ran into a problem: Ubuntu detects that my 250GB Drive is only 75GB big!!! 

Some more concrete info:

I can go to the Disks Manager and in the left side it detects my drive as a 250GB one, but in the when I select it. To the right, in the partition slot, it says that its only 75GB long.

I do not want to format it thats why I used G4L in the first place, but I dont know if formatting may be the only answer.Has anyone had this problem before? And what did you do?
-Thanks,
marko

Open a terminal and type:

```
df -h
```

Then, post the output here.

---

### Post by marko_4454 on 2006-08-27
> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   57G   11G  85% /
varrun                505M  148K  505M   1% /var/run
varlock               505M  4.0K  505M   1% /var/lock
udev                  505M  144K  505M   1% /dev
devshm                505M     0  505M   0% /dev/shm


This is what I get ...

---

### Post by infoseeker on 2006-08-27
Ghosting probably copied the partition size as well, so you will probably find that the space is there, but not being used.  Try using Gparted and resize the partition (needs to be unmounted, so use a live disk like the Ubuntu disk) if you need one partition.  You could, otherwise, simply create another partition using this free space with gparted and mount it using an entry in your /etc/fstab file.
Or simply use fdisk.

---

### Post by insane_alien on 2006-08-27
if you still have the PATA disk and it is intact put it back in format the SATA disk then either copy and paste all the files and go back through and delete what you don't want or just find and copy what you want to keep.

---

