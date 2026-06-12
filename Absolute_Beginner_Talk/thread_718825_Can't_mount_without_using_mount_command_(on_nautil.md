---
title: "Can't mount without using mount command (on nautilus)"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-03-08
If I go to nautilus and I try to mount a hard disk, it tells me

```
 You are not privileged to mount this volume 
```

But I can mount it using

```
 sudo mount /dev/hda1 
```

An help?

---

### Post by Duck2006 on 2008-03-08
This may help with linux

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

orwin

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by LuisGMarine on 2008-03-08
The reason is that when you launch nautilus it launches as a user, which in turn doesn't give you root privileges.

Would you likst to automount his hard drive on boot?  If so go ahead and make sure the drive is pluged in ( in case its a USB drive ) and run this command and give me the output of it.  

```
sudo fdisk -l
```

If not you are going to have to change the permission of the mount point.
```

sudo chmod -R [COLOR="Red"]username[/COLOR]:[COLOR="Red"]username[/COLOR] /path/to/mount/point

```

of course substitute [COLOR="Red"]username[/COLOR], for your actual user name.

---

### Post by psycardis on 2008-03-08
iirc the mount command requires su privs, therefore it needing sudo.

What exactly are you trying to do?

---

### Post by Fixman on 2008-03-09
> **psycardis said:**
> iirc the mount command requires su privs, therefore it needing sudo.

What exactly are you trying to do?

Im trying to mount an external hard disk, however, when I had Feisty Fawn I could mount correctly *when I double clicked it asked me for password, and then mounted. It also worked when I had Gutsy Gibbon 64-bit edition, but with Gutsy Gibbon 32-bit edition doesnt seem to work.

---

