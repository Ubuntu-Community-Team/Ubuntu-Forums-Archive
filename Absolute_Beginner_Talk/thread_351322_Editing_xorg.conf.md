---
title: "Editing xorg.conf"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by V3NOM on 2007-02-01
I know how to edit it with the X driver running, and I did so while installing drivers for my Nvidia card, which wouldn't work at all. I was running on the Intel i810 driver (my rather terrible integrated graphics, but at least they were working).

I needed to edit xorg.conf to finish the installation, but it turns out the driver didn't work. I edited the "nv" to be "nvidia"; while I was using the Intel driver it was "i810". I managed to reinstall the Intel driver using the apt-get command, but to finish so that it will work with the Intel again I have to edit the line in xorg.conf again to say "i810" once more. My X server won't start until I do.

Is there a command that I can use without the X server running to open the file for editing? The "gedit" command has only worked with X running. When I try "gedit" without X going it says something like "error starting display (null)"

---

### Post by shareMenaPeace on 2007-02-01
nano /etc/X11/xorg.conf

Works good fromthe command line too (eg. ALT F2 during boot)

---

### Post by Armor on 2007-02-01
From a terminal, type:

"gksudo gedit /etc/X11/xorg.conf"

Tada

---

### Post by psyne on 2007-02-01
** Just saw the double post sorry **

---

### Post by confused57 on 2007-02-01
You could probably boot into recovery mode & enter the  command mentioned in a previous reply:
```
nano /etc/X11/xorg.conf
```

you're logged in as root, so you shouldn't need to preface the command with "sudo".

---

### Post by aysiu on 2007-02-01
You want to use the command ```
sudo nano -B /etc/X11/xorg.conf
```

*sudo* allows you to edit the file even though it's a system (not a user) file.

The *-B* option creates a backup copy of the file before you edit. Backup copies of system files are **always** good to have before you go mucking around with them.

*nano* uses a terminal-based text editor to edit the file.

When you're done making your edits, save by pressing **Control-X, Y**, then **Enter**.

---

### Post by Daveth on 2007-02-03
so, can you get Ubuntu to re-detect and re-build the xorg.conf if one was stupid enough to overwrite the backup with a flawed backup? I'm having keyboard errors- sorry double posted this, but just found this thread which looks potentially useful for my problem.
Thanks in advance
David

---

### Post by Malac on 2007-02-03
> **Daveth said:**
> so, can you get Ubuntu to re-detect and re-build the xorg.conf if one was stupid enough to overwrite the backup with a flawed backup? I'm having keyboard errors- sorry double posted this, but just found this thread which looks potentially useful for my problem.
Thanks in advance
David
```
sudo dpkg-reconfigure xserver-xorg
```should do it.

---

### Post by Daveth on 2007-02-04
thanks -that fixed it. I will now copy the backup file to somewhere I will not over-write it!!!

---

