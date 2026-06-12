---
title: "screen resolution"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-07-27
I'm installing ubuntu on my desktop and it works fine on my laptop, but the screen resolution is off a little bit.  I went to system>preferences>screen resolution, and It didn't have a resolution big enough.  Is there a way to fix this?

---

### Post by bluecherry on 2006-07-27
You could manually edit your /etc/X11/xorg.conf file.

```

sudo gedit /etc/X11/xorg.confsudo gedit /etc/X11/xorg.conf

```

Add the desired resolution here;
```

SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480" "640x400"
EndSubSection

```

---

### Post by Zelut on 2006-07-27
You can run, from the terminal, 'sudo dpkg-reconfigure xserver-xorg' and select a larger resolution by hand.  If you've never used that before or are unsure about the options it presents you can safely use the default.

Just to be safe, run the following to make a backup before you make changes:
'sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-GOOD-BACKUP'

---

