---
title: "failed driver installation?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Bazzaah on 2007-04-24
Ok i admit it, I did something stupid and not for the first time.....

I wanted to install the new ATI drivers on my feisty installation but something has gone wrong as when I go into my feisty installation all I get is a black screen and a message from my screen telling me that 'input signal is out of range please reset to 1280x1024@60hz'. which would be fine if only it would display something aoart from that message from my screen.

I contemplated a reinstall but would rather not and that seems to me extreme remedy for what seems a failed driver installaton. I loaded up my Feisty disk to see if I could just write over the partition but no go it seems, it either attempts to create an extra smaller partition and fails or gives me the option of writing over everything, which includes my XP install, which I want to keep for some games.

So - is there a way i can get it up and running and visible again through recovery mode and what would be the terminal commands I would need to enter in recovery mode to get some kiind of display back?

in the meantime, very happy that I maintain a nice tidy Edgy installation!

Thanks in advance for your help

---

### Post by Paul41 on 2007-04-24
You can run this to go back to the default driver:

```
sudo dpkg-reconfigure xserver-xorg
```

If you do it in recovery mode leave the sudo off.  This will take you through some prompts to choose your settings.  For most things you can just select the default, but when you get to the video driver change from the ATI driver to the default one.

---

### Post by Bazzaah on 2007-04-24
excellent thanks for that - off to try it now!

---

### Post by Bazzaah on 2007-04-24
that did the trick - thanks v much for that!

---

### Post by Paul41 on 2007-04-24
No problem, good to hear you are running again.

---

### Post by Bazzaah on 2007-04-24
How can i tell which drivers my card is using?

if i do fglrxinfo  i get this 

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2


i would like to update to latest ATI drivers for some experiments in Wine, but when I try to iinstall restricted rivers module I am told that I don't need it.

Is there a way i can clear all drivers back to default installation out and start over? Is taht reconfiguring the xserver?

---

### Post by Paul41 on 2007-04-24
To see which driver you are using you can look at your xorg.conf file. It with be whichever one you chose when you reconfigured.  There may be some other command that will tell you this, but looking at the file is the only way I know.

```
gksudo gedit /etc/X11/xorg.conf
```

For the drivers try to reinstall them instead of a install.

---

### Post by AlexenderReez on 2007-04-24
it is better to backup your setting each time you want to try to change the setting...especially when it might corrupt your system...

---

