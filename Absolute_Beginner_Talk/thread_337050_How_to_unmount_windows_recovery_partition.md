---
title: "How to unmount windows recovery partition?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by mikewhatever on 2007-01-12
I dual boot on an HP Pavilion DV5000. Windows recovery partition gets mounted automatically, with permissions to create, delete and execute files. Obviously, these are the last things I want for that partition. I've tried looking here 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s02.html)
for answers, but, the funny thing is, I do not have Disks under System->Administration. What I wanted to know is:

1. How do I permanently unmount Windows recovery partition?
2. How do I prevent executing files in sda1 - Windows NTFS partition?

---

### Post by jvc26 on 2007-01-12
You dont have disks under there because that disappeared under Edgy (not sure why, I used to find it useful ;))

To permanently unmount you need to remove that partition from your fstab file, which is a file which contains all the data to mount each of your partitions.
[http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab](http://www.ubuntuforums.org/showthread.php?t=283131&highlight=how+to+fstab)
Is a very useful post on fstab.

To access fstab go to:
```

sudo nano /etc/fstab
**or**
gksudo gedit /etc/fstab

```
You need to ensure you are removing the right entry from fstab as removing the wrong one could land you in all sorts of interesting problems.

To temporarily unmount you would use terminal to:
```

sudo umount /dev/partitionname

```

Il

---

### Post by jd65pl on 2007-01-12
1. remove its entry from fstab and mtab

```
sudo nano /etc/fstab

sudo nano /etc/mtab
```

You can change permissions on a drive using chmod e.g.
 ```
chmod 777 /driveMount/point
```

See the link below for which options to use with chmod

[http://www.computerhope.com/unix/uchmod.htm](http://www.computerhope.com/unix/uchmod.htm)

---

### Post by mikewhatever on 2007-01-12
Thanks guys. Just unmounted the recovery partition and booted back. I hate editing system files. Just a note:

'sudo nano /etc/fstab' opens the file, but after deleting what I wanted, there was no save option

'gksudo gedit /etc/fstab' lets you both edit and save.

I'll read the tutorial to see if file execution can be disabled for Windows.

---

### Post by bodhi.zazen on 2007-01-12
LOL

With nano type Ctrl-X to exit. You will be asked if you want to save changes. Y = yes ; N = no

With sys config files:

[list=number][*]Backup first```
sudo cp /etc/fstab /etc/fstab.bak
```
[*]Don't delete a line, comment it out:> # /dev/hdxy /media/hdxy auto defaults 0 0# = Comments/notes


[*]If you add to a config file, use comments. Like this:> # Added by bodhi 1/2/07
# To mount my new hard drive

/dev/hdb1 /media/music auto users,auto 0 0
[*]You can also add comments at the end of a line> alias rm='rm -i'  # Adds confirmation to rm command[/list]

HTH 8)

---

### Post by mikewhatever on 2007-01-12
Thanks to all again. Uncommenting the line was definitely the way to go, I'll remember that for the future. As for backing up, there is no way I can recover the backup if something goes wrong. I am command line illiterate and after a month, there is no change. Don't know how you guys manage to memorize commands and location, and don't tell me it's just like DOS, because I am DOS illiterate too. :-D 

Anyway, things seem to work. I can boot into both Ubuntu and Windows, and the partition is unmounted.

---

### Post by bodhi.zazen on 2007-01-12
> **mikewhatever said:**
> As for backing up, there is no way I can recover the backup if something goes wrong.

Ahhh ... but we can (tell you that is).

> I am command line illiterate and after a month, there is no change. Don't know how you guys manage to memorize commands and location, and don't tell me it's just like DOS, because I am DOS illiterate too. :-D 

Anyway, things seem to work. I can boot into both Ubuntu and Windows, and the partition is unmounted.

CLI is just a matter of familiarity and use.

Start here: 

	[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
	[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)
	[http://www.justlinux.com/nhf/Command_Reference](http://www.justlinux.com/nhf/Command_Reference)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by mikewhatever on 2007-01-12
Hope you're right. Thanks.

---

