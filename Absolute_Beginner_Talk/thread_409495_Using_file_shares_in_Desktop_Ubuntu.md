---
title: "Using file shares in Desktop Ubuntu"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by novice1 on 2007-04-14
I have a simple question.  I have a small home network with two Ubuntu servers and one Ubuntu desktop and one Windows XP desktop. One of my servers is running Samba and I have been able to mount and use the Samba share from both desktops.  However I have been unable to either Open or Save files from/to the Ubuntu desktop when I am running any application. For example :The Samba Share is mounted on my Ubuntu desktop and contains an OpenOffice diocument I want to use. If I run OpenOffice, and select File, Open from the menu I can not find the Samba Share anywhere!  Conversely if i create an OpenOffice document and want to save it to the Samba share, I select File, Save and there is NO way to find the Samba Share.  I have tried typing the file path of the share and it still will not go to the Samba share at all. I type the exact path to the share with no results.  The only thing I have been able to do is save the file locally and then copy it to the Samba share. I can browse the Samba Share on the desktop and browse to a document and double click on it and it will open the document -- but it will not save the document back to the Samba Share.  This happens with all applications not just with OpenOffice. What is it that I need to do in order to use the share from within an application?

---

### Post by chalex on 2007-04-14
can you open a terminal and type "mount" and post the output?

---

### Post by novice1 on 2007-04-14
```
chuck@Shop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw,devgid=14,devmode=0660)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

This is the results if MOUNT -- however when I did this I curiously also was able to Open and Save documents from/to the share using OpenOffice -- so I am not sure what was going on. This was the first time I have been able to do that.  Thanks for your interest and willingness to help. \\Chuck

---

