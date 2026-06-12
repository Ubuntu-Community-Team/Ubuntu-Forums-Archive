---
title: "Edgy Logs out when opening .avi"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by scgriffiths2000 on 2006-11-08
Im trying to view an .avi, although when i try and open the file, it restarts X, no matter what program i use to view the file.

I have installed the latest Ati drivers 8.30.03 running on a ATI radeon x1900. Ive also installed all the Windows codecs etc.

Do you know why its doing it?

---

### Post by scgriffiths2000 on 2006-11-09
^^bump^^

---

### Post by aidanr on 2006-11-09
anything in /var/log/Xorg.0.log?
System->Administrarion->System Log

---

### Post by scgriffiths2000 on 2006-11-09
Nothing that relates to this problem I dont think.

---

### Post by scgriffiths2000 on 2006-11-09
Ive noticed that I can play the files using Songbird 0.2 but Totem, Mplayer etc just cause x to restart... If that helps?

---

### Post by aidanr on 2006-11-09
it seems songbird use vlc, if that helps any
you could try reinstalling stuff with synaptic, xorg, video drivers, mplayer, codecs etc
or use 
dpkg-reconfigure package_name
to reconfigure them
gl

---

