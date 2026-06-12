---
title: "Can't get visual effects / compiz working"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by transmition on 2009-04-26
I have been having a very horrible time trying to get compiz fusion working on my Macbook 4,1. Apparently my graphics driver got blacklisted during the upgrade to jaunty, but attempting to skip the blacklist check still fails.

I ran the compatibility script from here:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

and produced this output:
```
 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

So, it seems like things should work fine. So then I try
```

compiz --replace

```

Which produces:
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start

```

At this time, I cannot enable any visual effects. I head over to this thread, and follow the instructions, to see if I can get things working:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

So, now I can go into my appearance settings and select graphics options, they do not take effect. When I go to look at them, they are set back to "None"

In addition, the upgrading of the kernel from the last thread also disabled my wireless.

Someone please help me get compiz working. I *really* want to have a transparent terminal again.

---

### Post by transmition on 2009-04-27
*Bump and Update*

I downgraded my kernel, so my wireless is working again. I still can't activate any visual effects though.

---

### Post by -nat- on 2009-04-28
Have you tried the fix described [here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")... it looks like it could work.

I have the same graphics card in my Macbook 3,1, so I've had the same problem. No fixes have worked for me either :( but one of the has managed to disable my wireless.

> **transmition said:**
> *Bump and Update*

I downgraded my kernel, so my wireless is working again. I still can't activate any visual effects though.

Did you do a clean install? I'm also thinking of downgrading and was wondering what's the best way to do it?

---

### Post by pxwpxw on 2009-04-28
> **transmition said:**
> *Bump and Update*

I downgraded my kernel, so my wireless is working again. I still can't activate any visual effects though.

Is this what you tried to skip the blacklist

[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by transmition on 2009-04-28
Yes, I did.

---

### Post by transmition on 2009-04-28
> **-nat- said:**
> 
I have the same graphics card in my Macbook 3,1, so I've had the same problem. No fixes have worked for me either :( but one of the has managed to disable my wireless.
Did you do a clean install? I'm also thinking of downgrading and was wondering what's the best way to do it?

The last fix, upgrading the graphics, upgraded my kernel to an RC, and disabled my wireless. I reverted the change as it did not help.

I did do a clean install. At the moment, I would stick with 8.10 if I were you. Wait for the bugs to get ironed out.

---

### Post by transmition on 2009-05-01
Update: I did manage to get compiz working by installing beryl. However, after a time things started to get really slow and awful. I think I need to do the intel graphics fix to help this, but then my wifi drivers are removed, and I don't know where to get the broadcom driver.

---

