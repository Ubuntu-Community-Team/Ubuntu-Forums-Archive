---
title: "Mounting ntfs problem"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by Bigfootchris on 2005-07-16
I was able to mount my windows partition once but i haven't been able to get it to work since then.
So far i have made the directory for it (/media/windows) and i have added 
/dev/hda1	/media/windows	ntfs	nls=utf8,unmask=0222 0 0
to /etc/fstab so that it will mount at start up but now i get this error message:

wrong fs type, bad option, bad superblocke on /dev/hda1, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail or so

what could be the problem and how could i fix it?

thanks for any help

---

### Post by Umbra on 2005-07-16
I got that error to in command line many times, after checking several times i realize it that the problem was bad sintaxis, check if you're not mispelling some parameters.

---

### Post by Bigfootchris on 2005-07-16
i did, i must have retyped everything 20 time by now. I just don't have a clue of what to do.

---

### Post by Jussi Kukkonen on 2005-07-16
[QUOTE=Bigfootchris]I was able to mount my windows partition once but i haven't been able to get it to work since then.
So far i have made the directory for it (/media/windows) and i have added 
/dev/hda1	/media/windows	ntfs	nls=utf8,unmask=0222 0 0
to /etc/fstab so that it will mount at start up but now i get this error message:

wrong fs type, bad option, bad superblocke on /dev/hda1, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail or so

what could be the problem and how could i fix it?

thanks for any help[/QUOTE]
 that should probably be **umask**, not unmask.

---

### Post by GrootBrak on 2005-07-16
Darn, you stole my line!!! I had my "nsl" in stead of "nls", join the club.

---

### Post by dimension128 on 2005-07-30
My fstab line reads,
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

It appears to be working, If i go to /media/windows theres all my windows files.

But isnt there a way to get this new mount point to show up on the ubuntu desktop? 
Ideally in the "Places" menu, or Places --> Computer.

---

### Post by aysiu on 2005-07-30
[QUOTE=dimension128]
But isnt there a way to get this new mount point to show up on the ubuntu desktop? 
Ideally in the "Places" menu, or Places --> Computer.[/QUOTE] I don't know about getting it in the "Places" menu, but you can middle-click drag it to the desktop and select "link here," and a link will be created.

---

### Post by Omnios on 2005-07-30
This is how I have it set up.

```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
``` 

 Counting on what you have as woner and root etc it seems to show up in computer and other times it dows not. If you have your username as owner etc it seems that it does not show up. Think above is root as owner and groups as group. Might have to put your uername under groups of you have problems with it. SO far it has worked for me.

---

