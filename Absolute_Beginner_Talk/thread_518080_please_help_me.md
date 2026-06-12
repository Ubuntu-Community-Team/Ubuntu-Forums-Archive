---
title: "please help me"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by hnoverian on 2007-08-05
i just tried one of the commands dpg reconfigure ...as it was found in one of the threads about apt-get, then i went through the reconfiguration process and had two surprises. the first is that my screen resolution is fixed to become 1600*1200, the second surprise is that my desktop workspaces disappeared and the cube effect of feisty fawn has gone too. what could i do to get this effect again. i enabled the desktop effect and there is no way ,,,,, can anybody help me please......?????
thanks

---

### Post by Alexander2007 on 2007-08-05
> **hnoverian said:**
> i just tried one of the commands dpg reconfigure ...as it was found in one of the threads about apt-get, then i went through the reconfiguration process and had two surprises. the first is that my screen resolution is fixed to become 1600*1200, the second surprise is that my desktop workspaces disappeared and the cube effect of feisty fawn has gone too. what could i do to get this effect again. i enabled the desktop effect and there is no way ,,,,, can anybody help me please......?????
thanks

Open a terminal widow and type:
```
gconf-editor
```
  
Search for and modify as follows:
  ```
apps/compiz/general/screen0/options/hsize 4
apps/compiz/general/screen0/options/number_of_desktops 1
```

---

### Post by hnoverian on 2007-08-05
i followed this commands and i got the four desktop spaces but they r very slow and no effect while moving as when i installed ubuntu for the first time i can see the cube effect

---

### Post by Alexander2007 on 2007-08-05
> **hnoverian said:**
> i followed this commands and i got the four desktop spaces but they r very slow and no effect while moving as when i installed ubuntu for the first time i can see the cube effect

Try restarting, that should help, for the "no effect while moving" go to System > Preferences > Desktop Effects and enable "Windows Wobble when Moved" & "Workspaces on a Cube" and then repeat my previous post. (gconf-editor)

To make life easier (ie. configuring compiz) go to synaptic and search for "gnome-compiz-manager",  mark it for installation and apply it.
The menu item will appear in "System > Preferences > GL Desktop"

---

### Post by Tomosaur on 2007-08-05
It sounds like you used this command:

```

sudo dpkg-reconfigure xserver-xorg

```

Is this correct? If so, then you probably need to re-install the drivers for your graphics card, or at least reconfigure X to use these drivers.

If you can give us the following information, I'm sure someone can help out:

The make and model of your graphics card.
The contents of your /etc/X11/xorg.conf file.

If you're very lucky, there may be a backup of your old xorg.conf file. It will probably have a name with lots of numbers, and will be in your /etc/X11 directory. If there is one, then it may contain some of your old settings and such so that fixing the problem becomes a matter of copying and pasting the relevant parts.

Alternatively, you can just follow a guide to install Compiz Fusion - this should give you everything you need.

---

### Post by hnoverian on 2007-08-05
i tried installing the gnome-compiz manager and it somehow fixed the problem, but i feel that the movements in the whole screen is too slow i don't know why may be ubuntu is not accustomed to 1600*1200 resolution or maybe it is the refresh rate can you tell me why is the movement is too slow and i would simply try to add that i love ubuntu because of this forum no flattery.

---

### Post by sailor2001 on 2007-08-05
with your compiZ or beryl if in that, managers, you can speed-up, slow down. do anything you want..you own the machine. design it for the way you want...

---

### Post by hnoverian on 2007-08-05
> **sailor2001 said:**
> with your compiZ or beryl if in that, managers, you can speed-up, slow down. do anything you want..you own the machine. design it for the way you want...

ok i got the message but can u elucidate me, what can make the screen movements and icons change to become faster. thanks for help

---

