---
title: "screwed up cdrom mount"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by captainwitherspoon on 2007-07-29
Hello, I typed "mount /dev/cdrom /cdrom " into my terminal, I tried to install a game from a cd that didn't work. Now I have a CD-ROM 1 icon on the my computer window. How do I get rid of it?

---

### Post by DBStevens on 2007-07-29
Is the device still mounted?  

If it is unmount it.

---

### Post by captainwitherspoon on 2007-07-29
I tried
```
z@xZx:~$ umount  /dev/cdrom
umount: /dev/hdb is not mounted (according to mtab)
z@xZx:~$ umount  /dev/cdrom /cdrom
umount: /dev/hdb is not mounted (according to mtab)
z@xZx:~$ umount cdrom
umount: cdrom is not mounted (according to mtab)
z@xZx:~$ umount /cdrom
umount: /cdrom is not mounted (according to mtab)
z@xZx:~$ 

```
I found the fstab file but I can't make any sense out of it. There is an extra CD-ROM 1 icon on PLACES->COMPUTER. I can't access it or use it in any way. It's Location is Computer:///
It has 120GB of free space, weird. 

btw how do i check to see how much hd space I have left and run scandisk and defrag?

---

### Post by DBStevens on 2007-07-29
Sorry, I don't have a Places  >  Computer.  I don't run Gnome as my window manager. 

Could you provide the output from

cat /etc/fstab

and

cat /etc/mtab 


Some window managers show Icons for both mounted and unmounted devices, with only a slight difference between them.  In the case of KDE there is a little lighted corner if the device is mounted.  It has been at least two years since I've seen the Gnome equivalents.  There are also application programs that do it as well.

Is it possible that you did a copy and paste of the Icon I've seen that happen before with other systems?

---

### Post by captainwitherspoon on 2007-07-29
I've never seen this drive before, it definately happened when I tried to install that game.

```
z@xZx:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
z@xZx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=17802c1b-f084-4241-98a4-b627122b607e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=93755878-d534-43fe-bba8-e7a30b1b45dd none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by DBStevens on 2007-07-29
Ok.  I'm going to install Gnome while I wait for you to tell me which of the Ubuntu flavors you are running.  I'm assuming it is the Gnome based one however I have XFCE, KDE , and a couple of others already installed what's a few MB of disk space.

---

### Post by DBStevens on 2007-07-29
df in a terminal will tell you your free space etc...

---

### Post by captainwitherspoon on 2007-07-30
I think I'm running feisty fawn. Is that what you mean by flavor? I believe it's GNOME based.

---

### Post by captainwitherspoon on 2007-07-30
It's gone! 
I really appreciate your help, I don't know what happened but it seems to be solved.

---

### Post by DBStevens on 2007-07-30
Well I didn't actually do anything.

Yes the Gnome based is the flavor I was referring to, it is also helpful to know the release which would be Feisty Fawn.

I did install Gnome and tried to recreate the double device entry and couldn't either by mounting a cd or by trying several ways to possibly do a copy and paste.  

It seems from what you are saying that the second entry was more of an artifact than real.  Cute, I hate stuff like that.  Reminds me of web browsers and negative location specifications , you just never know where that content will end up ;-).

---

