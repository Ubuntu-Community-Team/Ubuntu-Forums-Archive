---
title: "You do not have permissions to write to this folder"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by nothingspecial on 2008-02-09
How do I change permissions for a little 4gig usb drive. It seems to be read only now but I`ve always been able to write to it before . I only use it to move music and photos etc between my pc and laptop.
 It is ntfs but I run 7.10 on both computers and writing to it has never been a problem.
  Any help greatly appreciated.

---

### Post by randy78 on 2008-02-09
I believe the easiest way to do this would be ALT+F2, then type gksudo nautilus, then navigate to the drive...

Should be good ;)

---

### Post by nothingspecial on 2008-02-09
Many thanks but it didn`t work.  Even in nautilus. ???

---

### Post by randy78 on 2008-02-09
you can try:
sudo mnt 'name of drive'

Example:
sudo mnt /dev/media/hda1/

---

### Post by seventhc on 2008-02-09
Try booting into windows and maybe you can check/change the permissions from there.
Before you do that, are you using *NTFS Configuration Tool*? If you are, there is a setting in there that turns on/off write capability and maybe it got switched somehow.

---

### Post by jan quark on 2008-02-09
run 

l```
s -l /patch to the usb drive
```

I guess somthing like
```

ls -l /media/...
```

and post the result, this will tell us the current permission set

you can change the permission with these commands

```
sudo chown -R usr:usr CU

sudo chmod -R 755 CU

s -la
```

CU must be replaced with the path to the directory or folder you want to change the permission and usr:usr must be changed to your username for instance john:john

---

