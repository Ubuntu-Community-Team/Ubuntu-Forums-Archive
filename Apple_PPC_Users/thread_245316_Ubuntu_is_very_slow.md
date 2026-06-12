---
title: "Ubuntu is very slow"
date: 2006-08-27
forum: Apple PPC Users
---

### Post by macfreaker on 2006-08-27
I've installed Ubuntu alternate cd on my G3 graphite.
I've a ppc 600mhz and 512mb ram in the system, but the system boots very slow (+/- 1 hour) and even after booting it takes very long to start a program (firefox 30 minutes). Anyone has a solution to speed up the startup of the system and programs ?
Thank you.

---

### Post by N8K99 on 2006-08-27
use synaptic to remove metacity - and install a lighter windows manager like xfce or blackbox. Or you could do this all from the command line.

---

### Post by 3rdalbum on 2006-08-28
A graphite G3 with 512 megs of RAm shouldn't be going so slowly.

Try going to the command line and typing:

```
sudo nano /etc/X11/xorg.conf
```

And "comment-out" (put the # symbol before) the four DRI-related lines:

```
#Load "DRI"

#Section "DRI"
# something or another
#EndSection
```

---

### Post by macfreaker on 2006-08-28
This is not working.
Any other idea ?  [-o<

---

### Post by macfreaker on 2006-08-28
> **N8K99 said:**
> use synaptic to remove metacity - and install a lighter windows manager like xfce or blackbox. Or you could do this all from the command line.

If i try to run the cdof xubuntu , i've the same problem.
I think that it is just something in the config file of the xserver,because is goes fine until the gnome or xfce starts. [-o<

---

### Post by didg on 2006-08-28
Do you have:
lot of drive activity? 
lot of messages in /var/log/syslog or /var/log/Xorg.0.log?

If you can run a terminal try top and look at the third line in the header:
Cpu(s): 92.5%us,  7.5%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

'us' should be low and 'id' high (mine is busy)

if us is high what are the first lines in the table?

---

### Post by 3rdalbum on 2006-08-29
I'm sure you've already tried this, but make sure that the only USB and Firewire devices plugged in are the keyboard and mouse, with the keyboard directly plugged into the computer.

---

