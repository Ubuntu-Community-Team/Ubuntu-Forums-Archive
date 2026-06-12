---
title: "I'm looking for some help on open/fluxbox customization..."
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-09-13
I'm trying to find a guide that details how you would get 2 terminals transparent (look like a part of the desktop) on the left side in the middle of the screen and another one on the right side in the middle of the screen.  I don't really want to use devils pie because whenever I mess with the geometry of it, it never ends up where I want it to.  Could someone recommend a program, etc. or guide that would let me achieve this.  Thanks.

---

### Post by felicity on 2007-09-13
You don't need devilspie if you use openbox, it has window placement features built-in. I use urxvt as my terminal, and use this line in my ~/.config/openbox/autostart.sh file:
```

# Programs that will run after Openbox has started
(sleep 1 && urxvt -name deskterm1) &

```

this starts up urxvt with the name deskterm1 after openbox starts. 

Then in my ~/.config/openbox/rc.xml file under Applications I can put:

```
    
    <application name="deskterm1">
      <desktop>1</desktop>
      <decor>no</decor>
      <layer>below</layer>
      <position>
        <x>-3</x>
        <y>+0</y>
      </position>
    <skip_pager>yes</skip_pager>
    <skip_taskbar>yes</skip_taskbar>
      <focus>yes</focus>
    </application>

```

You may not want yours to be precisely the same, but this should give you a general idea of the settings. Check the bottom of the rc.xml file for information on the settings you can use for window placement etc.

---

### Post by zetsumei on 2007-09-13
how would i get xrvt transparent? i'm liking xrvt btw LOL.

---

### Post by felicity on 2007-09-13
As far as I know there are two ways, one way is to check rxvt --help for the commands you want and use them in your startup file when calling an instance of rxvt. Another way, and the way I choose, is making an .Xdefaults file in your home directory. Then use this code:

```

rxvt*shading:          20

```
for how much you want it transparent (0 = no transparency, 100 = fully transparent)

and also this line:

```

rxvt*inheritPixmap:   true

```

to make the transparency show your desktop background.

---

### Post by RedSquirrel on 2007-09-14
I would just use the geometry option of the terminal itself to set size and position, e.g.,

```
urxvt -geometry 110x40+20+10
```Be sure to read the man page:

```
man urxvt
```

---

### Post by herbster on 2007-10-04
> **felicity said:**
> Then in my ~/.config/openbox/rc.xml file under Applications I can put:

```
    
    <application name="deskterm1">
      <desktop>1</desktop>
      <decor>no</decor>
      <layer>below</layer>
      <position>
        <x>-3</x>
        <y>+0</y>
      </position>
    <skip_pager>yes</skip_pager>
    <skip_taskbar>yes</skip_taskbar>
      <focus>yes</focus>
    </application>

```

You may not want yours to be precisely the same, but this should give you a general idea of the settings. Check the bottom of the rc.xml file for information on the settings you can use for window placement etc.

This is exactly what I'm looking for, Devilspie isn't working and I am running Openbox 3.4. Here's what I put in my rc.xml as an example to test with:

```
<!--
  <application name="xine">
    <decor>yes</decor>
    <shade>no</shade>
    <position>
      <x>center</x>
      <y>200</y>
    </position>
    <focus>yes</focus>
    <desktop>5</desktop>
    <head>0</head>
    # specifies xinerama head
    <layer>normal</layer>
    # 'above', 'normal', or 'below'
    <iconic>no</iconic>
    <skip_pager>no</skip_pager>
    <skip_taskbar>no</skip_taskbar>
    <fullscreen>no</fullscreen>
    <maximized>false</maximized>
    # 'Horizontal', 'Vertical' or boolean (yes/no/on/off/true/false)
  </application>
 -->
```

But it doesn't work. Must I log out and back in, or something else? Or my code may be incorrect? TIA!

---

### Post by string158 on 2007-10-15
I am running openbox with gnome-panels & whenever I press the desktop button everything is minimized including the terminal.

Is there any way to make this so that it is always on the desktop & doesn't minimize when the show desktop button is pressed????!?!?

---

