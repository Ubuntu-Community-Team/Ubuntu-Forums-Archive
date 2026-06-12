---
title: "Windows ran checkdisk, now Ubuntu won't load."
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by adamczar on 2006-12-18
I've spent roughly a week scrounging the internet, Googling things, and searching message boards to no avail.  I've found similar issues, but haven't really been able to find anything that matches my problem 100%, so thought I'd give this forum a try.

Basically, I installed Ubuntu 6.10 on a separate hard drive, as a dual-setup with Windows XP Pro on another drive.  Everything worked fine, until I booted back into Windows XP.  It ran it's "checkdisk," and during the last stage started deleting about five files.  I thought that was a strange thing do to, especially since it didn't ask (!), but nonetheless I failed to remember what files it deleted.

Later on, I tried booting back into Ubuntu, and it gave the following error:

"/bin/sh: can't access tty; job control turned off"

This is where the problem diverges from others I've found, because I have no command prompt and have to reboot the computer manually at this point.  I can get to GRUB and load Windows so I at least have some kind of OS.  I was also unable to find any posts linking the problem back to windows checkdisk.  I admit it's possible that checkdisk isn't the problem... I just found it strange that the trouble started after it deleted those files (without asking (!) )  :)

I tried booting into the recovery mode GRUB has listed, and it runs through some things then locks up before actually booting any graphical interface.  And I'm 100% new to all of this so get kind of lost easily.  :)

Thanks for any help... I'll keep at it, but thought I'd ask for opinions/ideas from a fresh (and probably more experienced) perspective.

---

### Post by urk_nono on 2006-12-18
I'm not sure, but this might be of help:

[LINK]("http://www.ubuntuforums.org/showthread.php?t=275728")

---

### Post by adamczar on 2006-12-18
Thanks!  Actually that might be a better way for me to go.  I'm thinking of reinstalling in such a way where I could boot using that method.

---

