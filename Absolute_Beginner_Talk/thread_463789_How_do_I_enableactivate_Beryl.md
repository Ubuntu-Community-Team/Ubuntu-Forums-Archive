---
title: "How do I enable/activate Beryl?"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2007-06-04
I downloaded it from the synaptic package manager and it installed with no problems. I open the  Beryl settings manager GUI and everything looks fine. So how do I enable the effects? My desktop is still normal (no effects).
My PC is a new notebook, Acer Aspire 5610, 2gigs and I'm using Ubuntu 7.04

---

### Post by steeleyuk on 2007-06-04
Does right-clicking the gem (tray icon), selecting Window Manager and then choosing Beryl not work?

---

### Post by blackened on 2007-06-04
First you'll need to make sure Beryl is even running. Right-click on the Beryl icon in the notification area, go to "Select Window Manager" and make sure the radio button for Beryl is active.

---

### Post by metalaxesucks on 2007-06-04
There is no Beryl icon in the notification area, What do I do?

---

### Post by zachalekos on 2007-06-04
Applications > System Tools > Beryl Manager

you can have it starting every time you login

---

### Post by dacookiemonn on 2007-06-04
you can also use the command:
```
beryl
```

---

### Post by metalaxesucks on 2007-06-04
I ran the command beryl and my computer would crash everytime. I'm just going to uninstall this thing and maybe try it another day. 
Thanks anyway for the help

---

### Post by blackened on 2007-06-04
Have you added the line

```
Option         "AddARGBGLXVisuals" "True"
```

into the "Screen" section of /etc/X11/xorg.conf?

---

### Post by metalaxesucks on 2007-06-04
> **blackened said:**
> Have you added the line

```
Option         "AddARGBGLXVisuals" "True"
```

into the "Screen" section of /etc/X11/xorg.conf?

I really don't understand what you are talking about. Do you mean type
Option         "AddARGBGLXVisuals" "True"
in the terminal? And where do I find the "Screen" section?
I'm still learning Linux, so I appreciate your patience
Thanks

---

### Post by bromix on 2007-06-04
Metal, what video card do you have, and I will post a link to a tutorial for you.

---

### Post by blackened on 2007-06-04
No worries, everyone has to start at the beginning. In the terminal type this (and remember everything is case sensitive)

```
gksudo gedit /etc/X11/xorg.conf
```

This will open the xorg configuration file in the gedit text editor. When it opens, scroll down to the "Screen" section of the file and cut-n-paste that line into that section. It should look similar (but not exactly mind you) to this

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"...
```

After that you'll need to restart the xserver by using
```
sudo /etc/init.d/gdm restart
```
in the terminal.

---

### Post by metalaxesucks on 2007-06-04
I followed these directions

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"...

And I still can't get beryl to work. And for bromix who needs to know my what kind of video card I have. I haven't the faintest idea, So I'm throwing in the towel for now. Thanks for your help. I'll try again some other day.

---

