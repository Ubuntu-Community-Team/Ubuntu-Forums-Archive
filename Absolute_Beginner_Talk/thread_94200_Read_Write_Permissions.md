---
title: "Read Write Permissions"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by steings on 2005-11-23
It seems that the default mode for Read & Write permission on my setup is Read Only on my Hard Drive.  I can see the HD fine, but everytime I try to download anything I get an error message that I don't have the proper permission.  It also happens if I try to copy from a CD to HD.  Any ideas where I can change this setting?  Thank You in Advance.

steings

---

### Post by endy on 2005-11-23
Can you post the contents of your fstab file? Just open it up in gedit and copy and paste it here.

```
gedit /etc/fstab
```

Is this your main hard disk or an extra disk / partition?

---

### Post by steings on 2005-11-24
Here my FSTAb file.  I had to post it through my XP Box as I don't have my USB Modem figured out yet.  I see the "ro" on the /dev/hda1 line. What should it say?  And yes this is my main and only HD.  This is an old DELL laptop that I'm playing with. Thanks for youer help.



# /etc/fstab: static file system information.

#

# <file system> <mount point>   <type>  <options>  <dump>  <pass>
proc        /proc           proc    defaults         0       0

/dev/hda1    / ext3    defaults,errors=remount-ro    0       1

/dev/hda5    none            swap    sw              0       0

/dev/hdc    /media/cdrom0   udf,iso9660 user,noauto  0       0

/dev/fd0  /media/floppy0  auto    rw,user,noauto     0       0

---

### Post by aysiu on 2005-11-24
Mine says this ```
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
``` and it still works fine. When you say it's read-only, which parts are you talking about? Did you know that the only files you'll be able to modify normally live in /home/steings? Anything else--/usr, /bin, /var, /boot, /etc--has to be modified by "root" or "sudo."

---

### Post by sarah_b on 2005-11-24
[QUOTE=steings]It seems that the default mode for Read & Write permission on my setup is Read Only on my Hard Drive.[/QUOTE]

You will have to type this command in a terminal to change your permission to read & write:

sudo chown your_system_username /path_of_files_or_folders

This works, but if you are not used to the Linux file system paths, it can be a little challenging.

sarah

---

### Post by steings on 2005-11-27
Thanks to all.  I thought it was strange to have to drop to terminal to save a file, move a file between one directory to another, or extract a file.  Although command line practice is always worth the effort, people new to Linux will find it bothersome.

---

### Post by sarah_b on 2005-11-27
[QUOTE=steings]Although command line practice is always worth the effort, people new to Linux will find it bothersome.[/QUOTE]

I agree with you, the desire to move to something better than MS Windows like ubuntu has to be a positive goal, and they may go back if they don't get help like using this great forums here and take the time to use ubuntu's documentation and how to's. It is worth the effort. Any Linux distro, even the worst one is better than MS..................OUCH !

I see MS is having adds on TV lately, this is new, one has to wonder why ?
Are they worried actually about open source and Linux.....if not, they should be !

---

