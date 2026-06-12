---
title: "Ubuntu won't change screen res."
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by chrispche on 2006-12-25
In system prefrences. Everytime I try to change the res to 800/600, It keeps logging me out and putting me back in 1024/768. Any ideas?

---

### Post by bodhi.zazen on 2006-12-25
What monitor and videocard ?

Try ```
sudo dpkg-reconfigure -phigh xserver-xorg

```Select the resolutions you want to use.


Restart X: Ctrl-Alt-Backspace or```
sudo /etc/init.d/gdm restart
```

If that fails, please post /etc/X11/xorg.conf

---

### Post by chrispche on 2006-12-25
I typed in what you said and the response I got was:

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061225213744

Any ideas?

---

### Post by Regel on 2006-12-25
I think that it's supposed to say that. Did it work?

---

### Post by bodhi.zazen on 2006-12-25
> xserver-xorg postinst warning: overwriting possibly-customised configuration
file; backup in /etc/X11/xorg.conf.20061225213744

LOL **warning** is such strong language ;)

No, this is normal. The "warning" is to alert you you have changed your xorg.conf and that you have a backup if needed (/etc/X11/xorg.conf.20061225213744).

Re-start x (Ctrl-Alt-Backspace) and check it out....

---

### Post by chrispche on 2006-12-25
No nothing happened and it did not give me the option of changing res.

---

### Post by bodhi.zazen on 2006-12-25
Please post your monitor, video card, and a copy of /etc/X11/xorg.conf

---

