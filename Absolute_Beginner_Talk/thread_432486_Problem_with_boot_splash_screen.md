---
title: "Problem with boot splash screen"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by look2 on 2007-05-04
Hi !

I did try to install another boot splash screen, but it didn't work out as I hoped.
I tried to install "Fingerprint" from [www.gnome-look.org](www.gnome-look.org). I followed the attached readme file. But When I booted the pc again it didn't work. I was only getting text, saying what the PC was doing. like:
"loading files needed for boot"

I started to mess around a bit, and all I get now is some kind of strange "test splash" It looks likes like the ones you sometimes can see on TV when there is no program. Like a test for the monitor.

Anyone know what I might have done wrong and how I can fix it ?
Edit/Delete Message

---

### Post by Kobalt on 2007-05-04
If you want to revert to the original splash screen you can reisntall the packages *usplash* and *usplash-theme-ubuntu*.

---

### Post by look2 on 2007-05-04
Just to apt-get install ? 
Anything else I need to change ?

---

### Post by look2 on 2007-05-04
After a reinstall I getting some text. Telling what modules and daemon's are starting...

---

### Post by Kobalt on 2007-05-04
Rather then using apt-install (which will tell you it's already install and do nothing) try using ```
sudo aptitude reinstall usplash usplash-theme-ubuntu
```

---

### Post by look2 on 2007-05-04
reinstalled it via synaptic, but maybe your alternetiv is better. Maybe you can tell me ehats wrong with this guide, why it won't work for me.

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

---

