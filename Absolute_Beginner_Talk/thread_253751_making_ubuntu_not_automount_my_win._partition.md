---
title: "making ubuntu not automount my win. partition?"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Watchintv on 2006-09-08
Hi there, I recently installed Ubuntu on my labtop (dual booted with windows).  I loved it but I decided to re-install it cuz I had been messing with it so much and wanted to start over.  So I popped in the install cd and set it to overwrite my ubuntu partition.  But my only problem is that this time it mounted my Windows partition and I didn't want it to do that.  So, I plan on going to re-install it again anyway (cuz I messed with it again, noob](*,)), but this time I don't want it to mount my Windows partition so if someone could tell my what I do in the setup part to make it not do this, that would be great.  Thanks!

---

### Post by jordanmthomas on 2006-09-08
I'm not sure I understand exactly.  When is it mounting the Windows partition?  After install or during install?  If it's during install, you really shouldn't worry about it.  If it's after installing, take a look in /etc/fstab and take out the part referring to your windows partition.

---

### Post by [S|G] on 2006-09-08
After install you could edit your /etc/fstab and comment out the line that points to your windows installating. That way it won't mount it again on the next reboot

---

### Post by Watchintv on 2006-09-08
I almost positive it's during install. Is it easy to unmount it once I have Ubuntu installed again?

---

### Post by jordanmthomas on 2006-09-08
Yes, once you get it reinstalled you can do this from a terminal:
```
sudo fdisk -l

```
note which one is your Windows drive
```

gksudo gedit /etc/fstab

```
find the line that refers to the Windows partition and put a # at the beginning of the line.
Close Gedit
```
sudo umount /dev/*whatever your drive is*
```
to unmount it without rebooting.  It shouldn't mount on your next reboot either.

---

### Post by [S|G] on 2006-09-08
Edit: look at the post above ;)

---

### Post by Watchintv on 2006-09-08
thanks, ill try it out

---

### Post by catlett on 2006-09-08
When you use the live cd for installation, it will take you to a page for mount points. It will have all your partitions listed. You probably pay attention to the root and swap partitions that have just been made but your windows partition will also be there. That is where it gets it's mount point. It will most likely be listed as /dev/hda1 and it's mount point is most likely /media/hda1. Just de-select the partition or delete the mount point /media/hda1 (or whatever it is) and make sure there isn't a value.
The above editing will work just as well. In fact it may be a better option because if you ever want to access your windows partition from ubuntu all you would have to do is open the file again and delete the comment mark #.

---

