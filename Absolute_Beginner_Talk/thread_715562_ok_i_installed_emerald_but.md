---
title: "ok i installed emerald but"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by slickh20 on 2008-03-05
ok its installed i have two themes sitting in the window and now i dont know what to do.  
i have compiz.
nothing changed on my desktop.

do i need to turn it on somewhere or what?  

is there an instruction on how to get themes going.

thanks all

---

### Post by JeffoOfMetal on 2008-03-05
compiz has to be changed to the default window manager

go to the terminal and type:

```
compiz --replace
```

it should take a second to kick in and then...

BAM! You're in compiz!

---

### Post by slickh20 on 2008-03-05
ok Awsome  it clicked over!!

but then all this showed up I know its because of my video card but any thing i should do about it?


casey@desktop2:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (blur) - Warn: No stencil buffer. Region based blur disabled
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by slickh20 on 2008-03-05
and now i have no top bar to any of the windows, i have the window decoration option chosen in compizconfig settings manager

?

---

### Post by slickh20 on 2008-03-05
got it

---

