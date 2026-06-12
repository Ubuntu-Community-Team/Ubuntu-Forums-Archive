---
title: "Backup Ubuntu OS"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2007-08-27
Hello. I was wondering how I can back up my entire Ubuntu configuration. I recently messed up Ubuntu and had to reformat and reinstall the OS. How can I back up all the configuration so that if I mess up, I have an already-configured PC to go back to?

---

### Post by solar george on 2007-08-27
[http://ubuntuforums.org/showthread.php?t=535669](http://ubuntuforums.org/showthread.php?t=535669)

---

### Post by sumguy231 on 2007-08-27
If you're concerned with keeping your personal configuration (preferences in apps, wallpaper, themes, etc.) then just make sure to back up your home folder; all of that stuff is stored in hidden directories in there. Systemwide configuration is kept in /etc, though most of that stuff you won't need to back up. The only thing I would suggest backing up in /etc is /etc/X11/xorg.conf if you've had problems with display settings.

Or, if you want to do it in a more "formal" manner use a backup tool like the one above.

---

### Post by Acglaphotis on 2007-08-27
Make a different partition for /home

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sumguy231 on 2007-08-27
> Make a different partition for /home
Highly recommended indeed. I have a separate home partition, and even if I reinstall I can be looking at the exact same desktop in no time at all.

---

### Post by bodhi.zazen on 2007-08-27
Well, to answer the question, you can back up with one of several options.

One is tar or rsync

or dd : [http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

Other options include 

Partimage : [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

Ghost for linux : [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

You could also look at clonezilla : [http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

There are several other options ...

---

