---
title: "Changing the resolution in ubuntu 6.10"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by tiptip on 2006-11-24
Hello, my first post here :KS 

I just installed ubuntu 6.10 and wanted to change the resolution,
i entered the "screen resolution preferences" but i noticed i was limited only to 1024x768 800x600 640x480.
After asking i been told to edit the /etc/X11/xorg.conf file and add 1280x1024 there.
I did and reset the system , now the screen does show in 1280x1024 (that what he writes when i press on the menu in the screen itself) but all the icons/ windows are showed in 800x600. also when i enter to "screen resolution preferences" i can choose only 800x600 and nothing else.

How i solve it ?

---

### Post by Bachstelze on 2006-11-24
Hi and welcome to Ubuntu :)

Do this :

```
sudo dpkg-reconfigure xserver-xorg
```

It will let you choose your resolution. It will also ask you a bunch of other questions, if you don't know what to answer, stick with the defaults :)

---

### Post by unbuntu kid on 2006-11-24
If you are using Intel 9xx chip, download the package 915resolution from Synaptic.

---

### Post by az on 2006-11-24
If it is an old card with very little ram, try lowering the color depth to 16-bit.

That would give you more memory to use higher resolutions.

If you are running a recent card, then that should not be the problem.

---

