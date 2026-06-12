---
title: "Lost alt+F2 function"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-10-19
I have suddenly lost the ability to bring up the run program using he Alt+F2 keys. I can't imagine how it happened. When I press the keys nothing happens.

---

### Post by Linux_Man on 2007-10-19
Are you using Beryl, Compiz, or Compiz-Fusion? Also, what window manager are you using?

---

### Post by cwrann on 2007-10-19
I am using gnome and compiz fusion. I have also lost my brown borders. All this seemed to have happened after trying to load an I-pod (Stupid Apple)

---

### Post by Dr Small on 2007-10-19
Have you tried turning compiz-fusion off, and see if the problem persists ?

---

### Post by cwrann on 2007-10-19
Honestly, the only way I kn ow how to turn compiz off is by using Alt+F2

---

### Post by Dr Small on 2007-10-19
I do not use compiz-fusion nor Gutsy (yet), but if you can turn it off by ALT+F2, then there must be some command you can run in the terminal to turn it off.

You should also be able to try:
```
ps aux | grep compiz
```

and see if you get any results. (You may have to mess with it, and try compiz-fusion or whatnot)
Then, run:
```
kill *pidnumber*
```

Dr Small

---

### Post by FuturePilot on 2007-10-19
Open a terminal and put in
```
metacity --replace &
```

---

### Post by cwrann on 2007-10-19
Is the Pid number the list of numbers that come after home when I run the first terminal command?

---

### Post by cwrann on 2007-10-19
I didnt relize that entering the smae commands in the terminal would have the same results as Alt+F2. I also didn't realize that Alt+F2 and compiz were linked.

I know that Metacity --replace will shut off compiz fusion so out of curiosity, to find out what happened to compiz fusion, I entered compiz --replace in the terminal and this is what I got.

```
home@home-desktop:~$ compiz --replace &
[1] 7904
Checking for Xgl: not present. 
home@home-desktop:~$ Detected PCI ID for VGA: 07:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/bin/sh: gtk-window-decorator: not found
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

Why would XGL and GTK window vanish. It worked fine for months?

---

