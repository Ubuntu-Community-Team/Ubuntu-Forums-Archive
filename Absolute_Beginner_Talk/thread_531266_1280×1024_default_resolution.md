---
title: "1280×1024 default resolution?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-08-21
How can I set my default resolution to 1280×1024? I can set it to 1280×1024 through nvidia-settings (run nvidia-settings in a terminal) and it works. But when X is restarted, I get 1024x768 again. How can I permanently set my resolution to 1280×1024?

Please help, izizzle

---

### Post by A3sthetix on 2007-08-21
hmmm... I know this issue... I came across it on my previous laptop. I'm still new to Ubuntu, but here is what I did in a nutshell:

- Installed the nVidia driver via restricted drivers
- Made sure my xorg file had nv instead of nvidia in it
- Rebooted

From there, you should be able to configure your resolution from within the Ubuntu GUI.

Give this a read:
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by Steve1961 on 2007-08-21
> **izizzle said:**
> How can I set my default resolution to 1280×1024? I can set it to 1280×1024 through nvidia-settings (run nvidia-settings in a terminal) and it works. But when X is restarted, I get 1024x768 again. How can I permanently set my resolution to 1280×1024?

Please help, izizzle

sudo gedit /etc/X11/xorg.conf

Then make sure 1280x1024 is in this section of the file:
```

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by asmoore82 on 2007-08-21
backup your /etc/X11/xorg.conf file ...

```
~ $ sudo cp -v "/etc/X11/xorg.conf" "/etc/X11/xorg.conf_$(date)"
```

and then edit the file "/etc/X11/xorg.conf," changing this section ...
```

        Defaultdepth    **24**
...
        SubSection "Display"
                Depth   **24**
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
```

to this ...
```

        Defaultdepth    **24**
...
        SubSection "Display"
                Depth   **24**
                Modes           **"1280x1024"**   "1024x768"      "800x600"       "640x480"
        EndSubSection
```

P.S. looks like I've been beaten to the punch!

---

### Post by r4ik on 2007-08-21
Had the same problem here fixed now.
Thanks. :popcorn:

---

### Post by izizzle on 2007-08-21
Thanks Steve! You fixed it! YAY! Now I am using my Geforce FX 5500 to its (almost) full potential!

---

### Post by fantasyspirit91 on 2007-08-21
I had the same problem too. I read a topic and it told me to save the configuration before restarting the X Server. It worked. =]

---

