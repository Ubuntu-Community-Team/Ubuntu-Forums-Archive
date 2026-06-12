---
title: "Driver install"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by marian_gacek on 2007-04-11
My display is not working right on fresh install of ubuntu , I have a cd with drivers for Linux
ext. "run" need a guide step by step how to install them.Thanks.

---

### Post by heimo on 2007-04-11
> 
    My display is not working right on fresh install of ubuntu , I have a cd with drivers for Linux
ext. "run" need a guide step by step how to install them.Maybe there is already drivers installed, but just not configured properly? What's the problem - too low resolution? What card / graphics chipset is it?


Could you open a terminal, run this command and give us the output? 
```
lspci | grep -i vga
```

---

### Post by marian_gacek on 2007-04-11
can't change resolution higher than 800 x 600

---

### Post by heimo on 2007-04-11
Yeah, I've seen that problem before. You should probably start by reconfiguring using this guide:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

If that doesn't help, it would be helpful if you could tell us a bit more details about your system: graphics card / chipset and monitor make and model. And if possible - open your xorg.conf file and paste us monitor section, screen section and device section.
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by DoubleQuadword on 2007-04-11
Another option could be 'reconfiguring' your xorg.conf file.

```
sudo dpkg-reconfigure xserver-xorg
```

Eventually, you'll be able to select which resolutions you want to add as well as the monitor's Vertical Refresh and Horizontal Sync. You should set those values according to what your monitor can actually support though.

Regards.

---

### Post by heimo on 2007-04-11
That's actually the same method as what I linked to. :)

---

### Post by DoubleQuadword on 2007-04-11
> **heimo said:**
> That's actually the same method as what I linked to. :)

You're right, I didn't check that link before posting. :)

---

