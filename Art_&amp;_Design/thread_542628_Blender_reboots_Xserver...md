---
title: "Blender reboots Xserver.."
date: 2007-09-04
forum: Art &amp; Design
---

### Post by [Alsharifi] on 2007-09-04
I installed Blender from synaptic y-day .

"sudo apt-get install blender"


it installed with no errors.


in the menu i have to options,full screen blender,and windowed blender.

when i click one of them my screen turns black and about after 5 seconds im at my login screen?

ive tryed a reinstallation but same thing happenes?


anyone have any ideas?

---

### Post by [Alsharifi] on 2007-09-04
no one?

---

### Post by FuturePilot on 2007-09-04
I think you need a 3D driver to use Blender.
What graphics card do you have?

---

### Post by [Alsharifi] on 2007-09-05
i have a radeon x300,im running compiz fusion fine.

i had blender,3dmax,cinema 4d working on windows.

---

### Post by [Alsharifi] on 2007-09-06
anyone?

---

### Post by [Alsharifi] on 2007-09-07
bump?

---

### Post by bwhitaker on 2007-09-09
This may be a silly question, but are you using the restricted ati drivers?

I just installed blender and it seemed to work fine for me.




Can you give us the output of the fglrxinfo command?


It should look similar to this:
```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

```

Also the proprietary ati driver from ati doesn't support compositing, so you may need to turn that off.

in your /etc/X11/xorg.conf at the very bottom, you may need to add

```

Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

---

### Post by zw0rk on 2007-09-09
This bug is in blender's bugs repository. The problem is in ati driver. Maybe, driver-update will fix this problem.

excuse me my poor english

---

### Post by [Alsharifi] on 2007-09-09
i think i figured it out.Im running fglrx+xgl which wont allow me to enable direct rendering..this sound correct?

---

### Post by zw0rk on 2007-09-09
> **'[Alsharifi] said:**
> i think i figured it out.Im running fglrx+xgl which wont allow me to enable direct rendering..this sound correct?

[Here is link to this bug in blender's "bugzilla"](http://projects.blender.org/tracker/?group_id=9&atid=125&func=detail&aid=5983).

---

### Post by [Alsharifi] on 2007-09-09
```
Apparently fglrx needs to be manually updated on each kernel
update
```

how would i do that?

---

### Post by bwhitaker on 2007-09-09
I believe the driver is provided by the linux-restricted-modules-generic package.  Which, if installed, should be updated automatically at the same time as the main kernel package.

---

### Post by Blara on 2007-09-10
I have another problem with Blender, it starts ok, both windowed and fullscreen. But I can't access the menus (file, add, etc etc) when I click them nothing happens. Anyone have any idea?

---

### Post by [Alsharifi] on 2007-09-10
thanx for hijacking my thread :P..

j/k i gave up on blender!

---

