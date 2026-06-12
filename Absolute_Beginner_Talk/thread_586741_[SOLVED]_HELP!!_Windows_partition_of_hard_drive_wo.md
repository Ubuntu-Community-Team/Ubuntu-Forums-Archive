---
title: "[SOLVED] HELP!! Windows partition of hard drive won't mount"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-22
My Dell Latitude D620 has its hard drive partitioned in half for a 7.10/XP boot.  When I turned on my computer today, Windows will not boot.  It gives me a blank black screen when the Novell client should load.  I can't mount and access the Windows partition out of Ubuntu.  I receive the following error message:(abbreviated by me because I cannot copy the text)

Logfile indicates unclean shutdown(0,0).  NTFS is marked to be in use.  Choice 1: If you have windows, safely remove hardware(this is for an external device, I have an internal disk)
Choice 2: use the force option     mount -t ntfs-3g /dev/sda2 /media/disk -o force

I tried to force mount 
```
$ sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda2 ()
```




Please help, I have a paper due soon on this hard drive and I need to print it out!!!

---

### Post by magli on 2007-10-22
What happens when you try to boot windows?

Did you try using the force mount option?

---

### Post by iamthemicrowave on 2007-10-22
Yes I tried force mount. Updated first post.

When I try and boot Windows I get a blank black screen where the Novell Client should load for me.

---

### Post by mikeyphi on 2007-10-22
> **iamthemicrowave said:**
> 

I tried to force mount 
```
$ sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
fuse: failed to access mountpoint /media/disk: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda2 ()
``` 

Try to make a directory, then force mount again:

sudo mkdir /media/disk

---

### Post by iamthemicrowave on 2007-10-22
Thank you so much, what an easy solution!!! Any advice for getting XP working?

---

### Post by magli on 2007-10-22
> **iamthemicrowave said:**
> Thank you so much, what an easy solution!!! Any advice for getting XP working? Wrong place for that :)

---

### Post by mikeyphi on 2007-10-22
I'm not familiar with the "Novell Client" but in the old days (!!) I would use a windows CD, access the recovery console and take it from there.

It seems as though you can boot into windows but that there is a file problem during the process - perhaps a windows CD and run a disk check?

---

### Post by Death Rider on 2007-10-31
> **magli said:**
> Wrong place for that :)

Hahaha :D I doubt that windows forums would help :D (p.s. dunno if windows have forum :D )

---

