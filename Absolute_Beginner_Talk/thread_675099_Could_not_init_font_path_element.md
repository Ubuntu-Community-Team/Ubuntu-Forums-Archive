---
title: "Could not init font path element"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by markoklacar on 2008-01-22
Hello,

when I try to start X using startx I get the following error:

Could not init font path element

The machine I'm trying to do this on runs Ubuntu server.

Any help is greatly appreciated.

Thanks

---

### Post by mali2297 on 2008-01-24
It probably means that you need some extra package. Have you installed the meta package [xorg]("http://packages.ubuntu.com/gutsy/x11/xorg")? (Several fonts packages seem to come with it.) 

Also, run 
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by markoklacar on 2008-01-24
The package was already installed :confused:, after the reconfiguration I get this error:

XIO: fatal IO error 104.....

I've tried reading some posts with the same problem, here's what I've done:

sudo dpkg-reconfigure xserver-xorg
choose Vesa
remove all resolutions except 640x480
set "HorizSync 36-52" and "VertRefresh 36-60"
startx

Any help is appreciated...

Thank you...

---

