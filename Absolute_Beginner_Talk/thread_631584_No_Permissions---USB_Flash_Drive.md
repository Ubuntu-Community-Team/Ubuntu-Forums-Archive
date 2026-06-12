---
title: "No Permissions---USB Flash Drive"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by uboodumdum on 2007-12-04
My 80 gig WD external is fine, I can read and write but the lil flash is read only.  I'm using NTFS not Fat.

---

### Post by vikram on 2007-12-04
check permission on the flash drive. can you write as root ?

also you here are the instructions to allow *buntu to read and write NTFS

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by uboodumdum on 2007-12-04
Thanks, when you check permissions everything is greyed out, no way to even use the drop down box, I will do some more reading, I have your link and a cmod tutorial

---

### Post by uboodumdum on 2007-12-04
I can mount the drive, it's just worthless, can't copy or delete files, can read what is on it now

---

### Post by vikram on 2007-12-04
> **uboodumdum said:**
> Thanks, when you check permissions everything is greyed out, no way to even use the drop down box

this probably means you dont have permissions. 

you can try accessing it as root as follows:

a) in the terminal you can use this command

```

sudo touch /media/wherever-your-flash-drive-is-mounted/dummyfile

```b) 
```
kdesu konqueror
``` (if you use KDE)

c) ```
 gksu nautilus 
```(i think this works in GNOME not 100% sure)


if you still cant write or delete you need to install the ntfs 3g, see link in my post above

---

### Post by uboodumdum on 2007-12-04
I can mount the drive, it's just worthless, can't copy or delete files, can read what is on it now

---

### Post by uboodumdum on 2007-12-04
Ok, thanx:KS

---

### Post by chitowner on 2008-06-19
Since this is an old thread I hope someone helpful will notice my post. I am a new member so if this should be in another forum please advise.

I have a USB flash/thumb/key that has somehow gotten whacked. It reports as "read only" and had a large amount of corrupted files so I did 
~$ mkfs.reiserfs /dev/sdd1 -f
but now, when it is remounted, it is owned by root.

I would like to know how to have USB keys "owned" for 777 access by the current (or designated) user when they are mounted.

Can someone propose a shell script that would essentialy prompt the current user, when a USB thumb is connected, whether to mount for the current user or for root?

Thanks

---

