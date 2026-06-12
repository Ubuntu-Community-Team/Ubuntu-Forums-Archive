---
title: "Changing properties on mounted drives"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2005-12-21
I would like to change the properties on a mounted drive I have, except the options of "read only", "write only", and "execute" are grayed out.  It says that I am not the owner and do not have permission.  There is only one login on my computer, and I don't know how to login any other way.  Is there any way I can go through the terminal using sudo to access those properties?  Thanks.

---

### Post by aysiu on 2005-12-21
What kind of drive is it? Windows partition? External USB drive?

---

### Post by Iandefor on 2005-12-21
open up a terminal and type in ```
gksudo nautilus
``` it'll ask you for a password; just enter the one for your currently logged-in account. You 
should be able to change the permissions now.

---

### Post by jbmalone on 2005-12-21
Well, it was my iPod and I have been having trouble with gtkpod.  It keeps saying that the database file does not exist, when it does.  So I thought maybe the permissions were incorrect.  Thanks for your help, you guys.

---

### Post by aysiu on 2005-12-21
Two things at issue here:

#1. Mounting with the right permissions. See the fourth link in my sig. It's probably /dev/sda1, but you should check.

#2. Gtkpod. Gtkpod assumes your iPod is mounted at /media/ipod or /mnt/ipod (I can't remember which). You can change the mount location in Gtkpod preferences (just poke around). You could also change the mount point for the iPod.

---

### Post by jbmalone on 2005-12-21
Yeah, I tried fixing the mount point, but that didn't help.

---

### Post by Iandefor on 2005-12-21
How has your ipod been formatted? In other words, how did you get music
on your ipod before; with a Mac or Windows computer? If it was with a Mac,
you need hfsutils and hfsplus. to get those, open up a terminal and type in
```
sudo aptitude install hfsutils hfsplus
``` Oftentimes, that's
the source of most trouble with Ipods. If it was with a Windows computer,
I've found that [YamIpod]("http://www.yamipod.com/main/modules/home/")'s pretty good. Dunno if that'll help much, though.

---

### Post by jbmalone on 2005-12-21
It was with a Windows computer, and I tried YamiPod and followed their installation guide but the program would never open up.  I copied the lib file into the /usr/lib directory and then clicked on the binary as instructed and nothing happened.

---

