---
title: "i'm sure it is easy, but i can find it in the forums...."
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-11-12
hello,
I figure this is simple but i can't find it on the forums.
When i installed ubuntu i had it mount hda1 (winXP NTFS) to /media/hda1 and it shows up on my desktop and it is there every time i boot up and all that like it is suppose to.  the problem is it's NTFS and i have no need to get to it from ubuntu.  how do i make it stop mounting on startup?

---

### Post by jordanmthomas on 2006-11-12
press Alt + F2
type
```
gksu gedit /etc/fstab
```
And remove the line that mentions the NTFS partition

It won't mount on next boot.
To unmount it immediately, run 
```
sudo umount /dev/hda1
```
in a terminal

---

### Post by bodhi.zazen on 2006-11-12
Or add a # at the beginning of the line. Thus you'll have it (for referance)if you need it.

---

### Post by jordanmthomas on 2006-11-12
indeed.

---

### Post by insub2 on 2006-11-12
beautiful!

---

