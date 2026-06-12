---
title: "X Crash--Beryl--Please Help"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-06
I installed beryl using the instructions here: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

After rebooting I am unable to get the gui back, and I'm nearly helpless without it.  I did restore /etc/X11/xorg.conf from the backup using the command line, but it didn't help.  I foolishly put beryl and emerald in the startup list, and I don't know how to find that and change it.  Running Dapper 6.06.

All help appreciated.

Buck

---

### Post by klayn on 2006-12-08
The ultimate newbie solution (the one that I used when the same thing happened to me) was "sudo apt-get remove ubuntu-desktop" followed by a "sudo apt-get install ubuntu-desktop"...

Hopefully someone more knowledgeable can answer this too, but if not, that's the easy way...

---

### Post by bodhi.zazen on 2006-12-08
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then re-startx:```
sudo gdm
```

Or reboot

---

### Post by Buck2348 on 2006-12-08
Thanks very much for your replies.  Apparently there's more than one way to skin a cat.  I fixed it with "sudo apt-get install xserver-xorg-core-1:1.0.2-0ubuntu10".  Soon after that I tried to upgrade to Edgy and broke it again, and this time couldn't fix it, so I did a full install of Edgy.  I appreciate your help.  Happily I was able to get my network working with the same method I used in Dapper.

Buck

---

### Post by jubxie on 2006-12-10
if anyone else has this prob(like I did), you could also login to the terminal and edit/delete these entries in 

~/.config/autostart

---

