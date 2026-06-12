---
title: "nVidia glx problem - can't turn composite off"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by KameZero on 2008-02-12
So, I just reinstalled ubuntu to the latest version, everything works great so I install the nvidia-glx-legacy drivers, edit xorg.conf to use them and restart gdm, everything works, However, I discovered that glx is in fact not functioning. After searching a bit I found I needed to disable composite, however, everytime I put
```
Section "Extensions" 
        Option  "Composite" "Disable"
EndSection
```
at the end of my xorg.conf and start gdm back up it completely fails to start with no error showing after I choose yes at the prompt. Any help would be greatly appreciated.

---

### Post by KameZero on 2008-02-12
Come on, somebody has to know something. Please.

---

### Post by jordanmthomas on 2008-02-12
Instead of putting the DIsable part in there, just try removing the whole extension section.  Composite will be disabled at this point.
(You can put # in front of each line so you don't forget what was there)

You can edit in by hitting ctrl - alt - F1 and logging in, then
```
sudo nano /etc/X11/xorg.conf
```
Ctrl - O will save, then hit enter, then Ctrl - X and try restarting gdm
```
sudo /etc/init.d/gdm restart
```

---

### Post by KameZero on 2008-02-12
There isn't an extension section as far as I can see. Apparantly composite is enabled by default or somesuch.

---

