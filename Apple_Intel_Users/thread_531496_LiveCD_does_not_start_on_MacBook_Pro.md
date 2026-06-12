---
title: "LiveCD does not start on MacBook Pro"
date: 2007-08-21
forum: Apple Intel Users
---

### Post by nyakasc on 2007-08-21
Hi,

I've just got a new MacBook Pro. I tried to install Suse on it but had enough of hacking the whole thing together. Hence I downloaded Ubuntu 64 bit LiveCD. Unfortunately it dies during install.
It blanks the screen and stops after I choose install from the boot menu. I tried to alter the settings by pressing F6. Deleted the last two parameters (quite splash  --) and now I can see that it tries to get the kernel up, but fails mounting ext3. It prints below 10 time :

kjournald starting, Commit interval 5 seconds
EXT3-fs:mounted filesystem with ordered data mode.

and drops in a shell.  It seems to be the initial ram drive.

Any hint on how to go from here?

---

### Post by cyberdork33 on 2007-08-21
try the alt install cd. The x server crashes with the ATI hardware.

---

### Post by macaholic on 2007-08-21
Ya, you can only install from the alt cd on most macbook pros, I blame ati's crap drivers.

---

### Post by nyakasc on 2007-08-21
Thank, but It has nothing to do with the graphics card. The problem is that it cannot mount the root partition hence cannot finish setting up the install environment. 

Also being a new MacBook Pro it has an nvidia card.

---

### Post by cyberdork33 on 2007-08-21
> **nyakasc said:**
> Thank, but It has nothing to do with the graphics card. The problem is that it cannot mount the root partition hence cannot finish setting up the install environment. 

Also being a new MacBook Pro it has an nvidia card.

Your 'error' does not indicate that the filesystem has not mounted, in fact, it is telling you that it has mounted the filesystem. If you have an error that led you to believe that was the issue then please post it.

There are also issues with the Santa Rosa machines. please see the Santa Rosa thread for help on getting things working.
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

