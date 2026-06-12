---
title: "Low Graphics, Gutsy, dv6000"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by kd5tmu on 2008-01-09
I have a dv6000 series HP lappy, and I have been running Gutsy for over 2 months.  Today, when trying to get my built-in webcam to work, and my touchpad not to be so touchy, I restarted to find my computer in LGM with none of my special settings from Compiz available.  Nothing I can find has helped me, it won't come out of LGM. 

Please HELP!

---

### Post by lian1238 on 2008-01-09
Try this.
```

cd /etc/X11/
dir

```
You'll probably find some backup files of xorg.conf in there somewhere, usually with the name xorg.conf.<date> or xorg.conf_backup_<date>. Try replacing xorg.conf with the different backup files, going to the latest backup file.
```

sudo cp xorg.conf.example_backup xorg.conf

```
(You may want to use TAB to auto-complete the file names. Just a hint.)

Now restart X, Ctrl+Alt+Backspace.

---

### Post by kd5tmu on 2008-01-25
Thanks!  Sorry it took so long to get back, been dealing with other issues.  I eventually got it figured out though.

Now if I can only figure out this vlogging thing....

---

