---
title: "monitor dead pixel question"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Diiblo on 2006-03-29
I just installed unbuntu for the first time and my monitor said it should be used at 1600x1200 and 60hz so I put it at that but i see seem to be seeing what looks like dead pixels sometimes on the desktop after minimising or closing something then it will just go away.. they pop up all over the desktop..

does anyone know what this is?

---

### Post by taurus on 2006-03-29
You may want to check the horizontal and vertical refreshing rates in /etc/X11/xorg.conf then...  If you need to edit it, run this command from the terminal, backing up the original file first in case you need to bring it back.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf

```

---

### Post by Diiblo on 2006-03-29
[QUOTE=taurus]You may want to check the horizontal and vertical refreshing rates in /etc/X11/xorg.conf then...  If you need to edit it, run this command from the terminal, backing up the original file first in case you need to bring it back.
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf

```[/QUOTE]


I dont see anything about refresh rates.. its a LCD if that matters..


I see "SyncMaster"
option   "DPMS"
Defaut depth 24 then it does 1,4,8,15,16, and 24 showing different modes

---

### Post by taurus on 2006-03-29
I have a LCD monitor, Dell Optiplex GX620, and I have these lines in my /etc/X11/xorg.conf...
```

        HorizSync    30.0 - 81.0
        VertRefresh  56.0 - 76.0
        Option      "dpms"

```

---

