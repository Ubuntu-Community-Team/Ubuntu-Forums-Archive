---
title: "Visual Effects don't work after Amarok"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by lohnew on 2007-12-23
I just installed Amarok and all my visual effects don't work. I tried opining my Compiz manager settings, they don't open! I un-installed Amarok in synaptic package manager but still no effects and i cant open the Compiz manager! Im running Ubuntu 7.10.


Thanks,
Westin

---

### Post by Nano Geek on 2007-12-23
Run this in the terminal and tell me what it says.```
compiz --replace
```

---

### Post by lohnew on 2007-12-23
westin@Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0241 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by RomeReactor on 2007-12-23
Hi. Do you have an ATI card? it looks like XGL is not installed; try to install it and then see if you can enable Compiz:
```
sudo apt-get install xserver-xgl
```

EDIT: Sorry, didn't notice you have an nVidia card. Try running these commands in the terminal:
```
glxinfo | grep rendering
```
and
[CODE]cat /etc/X11/xorg.conf | grep Driver
if ti says no, and the last driver the second coomand lists isn't **nvidia**, then you can't enable the effects until you use the proprietary driver.

---

### Post by lohnew on 2007-12-23
This is what i got

```
westin@Ubuntu:~$ glxinfo | grep rendering
direct rendering: Yes
westin@Ubuntu:~$ cat /etc/X11/xorg.conf | grep Driver
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"
westin@Ubuntu:~$ 
```


I couldn't understand what you meant after you said to put in cat /etc/X11/xorg.conf | grep...i am a complete noob.

---

### Post by RomeReactor on 2007-12-24
Since you're using the nvidia driver and you have direct rendering enabled, you *should* be able to run Compiz; I don't see how installing Amarok could have messed that up, unless you installed the Kubuntu desktop package and are running in KDE. I you *are* in KDE, logout, start a Gnome session and see if you can enable Compiz then.
Also try opening Synaptic, and in the lower left part press the "Status" or "Custom Filter" buttons and see if you have an entry there for 'broken packages'; if you do, highlight it and see if there are any packages listed. If there are packages listed there, close Synaptic and from the terminal run:
```
sudo apt-get install -f
```

Then see if after that you can open Advanced Desktop Effects Settings and start Compiz.

---

