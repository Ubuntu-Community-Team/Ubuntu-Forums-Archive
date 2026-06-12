---
title: "Beryl &amp; iMac"
date: 2007-07-12
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-07-12
Hi All!

I have installed beryl on my iMac Intel (with Mobility Radeon X1600), Feisty 64bit, KDE desktop.
But:
1) GUI works veeeery slow.
2) Kkbswitch shows three! languages (called '1', '2' and '3') instead of Russian and English.
3) When I run beryl-manager and then beryl-xgl, white screen shown and alt-tab works, but it works very strange: only shadows of windows and those icons are visible.

Here are my scripts:
```

[root@Ubivetz:~] cat /usr/local/bin/startxgl.sh
#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
sleep 2
exec startkde
#exec dbus-launch --exit-with-session gnome-session

[root@Ubivetz:~] cat /usr/local/bin/start_beryl.sh
#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl --use-copy
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

[root@Ubivetz:~] cat /etc/X11/sessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application                           

```

---

### Post by cyberdork33 on 2007-07-12
I used this how to to get it all working on mine.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

The fglrx portion is the second half of the section.

Since you are on kde, I am unsure what needs to be different.
your startxgl script looks ok, although I don't know if you need the cookie part. (that is only if you are missing restart and shutdown buttons in gnome.)

Your start_beryl script seems kind of unecessary to me... once XGL is running and your desktop environment is up, you should just have to run beryl-manager to get everything going.

BTW, the slowness maybe coming from the --use-copy part

The Beryl How To gives differences for KDE, so you might try there too
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

From the last link I posted. This should be all you need instead of the start_beryl script.
> 
**KDE** 
  Add **beryl-manager** to KDE's autostart. Open a terminal and create the following symlink: 
 ```
$ ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager
```

---

### Post by Ubivetz on 2007-07-12
> **cyberdork33 said:**
> I used this how to to get it all working on mine.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
BTW, the slowness maybe coming from the --use-copy part

The Beryl How To gives differences for KDE, so you might try there too
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

From the last link I posted. This should be all you need instead of the start_beryl script.
No, I was misunderstood; XGL **without Beryl running** works slooooow. ](*,)

---

### Post by cyberdork33 on 2007-07-12
> **Ubivetz said:**
> No, I was misunderstood; XGL **without Beryl running** works slooooow. ](*,)


I don't know what to tell you there. There is utterly no difference for me. maybe uninstall and start over...

You do have fglrx working right?

---

### Post by Ubivetz on 2007-07-12
```

$ cat /var/log/Xorg.0.log | grep '(WW)'
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "AddARGBGLXVisuals" is not used
(WW) fglrx(0): Option "RenderAccel" is not used

```

---

### Post by Ubivetz on 2007-07-12
> **cyberdork33 said:**
> I don't know what to tell you there. There is utterly no difference for me. maybe uninstall and start over...

You do have fglrx working right?

```

$ glxinfo | grep direct
direct rendering: Yes

```

---

### Post by cyberdork33 on 2007-07-12
what is the output of fglrxinfo.

---

### Post by cyberdork33 on 2007-07-12
oops. double post.

---

### Post by Ubivetz on 2007-07-12
```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)

```

I have also added the following to me xorg.conf:
Section "device"
&#8230;
Option "XaaNoOffscreenPixmaps"   "1"
....
Section "Extensions"
Option "Composite"   "0" 
Option "RENDER"   "Enable"
EndSection

with no result

---

### Post by cyberdork33 on 2007-07-12
It looks as though everything is running correctly with fglrx.

The composite option should go in it's own section I believe:
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```

---

### Post by Ubivetz on 2007-07-13
> **cyberdork33 said:**
> It looks as though everything is running correctly with fglrx.

The composite option should go in it's own section I believe:
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```
It doesn't matter, in which section it is located, :(   as the metter of fact it works sloooow in any case. Unfortunately, I have no idea how to fix it. At home, I'm using ordinary PC with RadeOn X600 and Beryl works with it very fine (Mandriva 2007.1, glx drivers).

---

### Post by cyberdork33 on 2007-07-13
> **Ubivetz said:**
> It doesn't matter, in which section it is located, :(   as the metter of fact it works sloooow in any case. Unfortunately, I have no idea how to fix it. At home, I'm using ordinary PC with RadeOn X600 and Beryl works with it very fine (Mandriva 2007.1, glx drivers).

Well, I have exhausted about anything I can think of. It might be time to start over and try again. It seems that it is a problem with XGL itself and nothing else. good luck.

---

### Post by Ubivetz on 2007-07-16
When XGL is running
```

$ glxinfo  | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

```

---

### Post by cyberdork33 on 2007-07-16
That's normal. No issue.

---

### Post by Ubivetz on 2007-07-17
New circumstances have been found.
I switched to the first console (Ctrl-Alt-F1) and then type
```

$ sudo bash
# /etc/init.d/gdm stop
# Xgl :1 -fp /usr/share/fonts/X11/misc -ac -accel glx:pbuffer -accel xv:pbuffer -br &

```
Just wait until black screen with X-cursor appeared. And type at the second console:
```

$ sudo bash
# DISPLAY=:1 konsole

```
And type in the konsole:
```


P.S.

# mc

```
Mc worked fast, then I exited mc and tried 
```

# start_beryl.sh

```
White rectangle (with size equal to konsole window size) appeared. **Cube worked!**
Hm, what's wrong?
Then I killed Xgl and started it again, but instead of run konsole, I tried to run whole KDE:
```

$ sudo bash
# DISPLAY=:1 startkde

```
KDE start loading, but hang for the middle. Then I tried to load GNOME
```

$ sudo bash
DISPLAY=:1 /usr/bin/gnome-session

```
Gnome started ok, but XGL started working slooooow :confused:
```

$ cat /usr/local/bin/start_beryl.sh
#!/bin/bash
#
# Start beryl-manager within gnome-session
#
if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

```

---

### Post by cyberdork33 on 2007-07-17
DISPLAY=:1 beryl-xgl

Don't do that.

start Xgl, start kde or gnome or whatever, then just do 
'beryl-manager' that is it. you do not need the script. You should get a emerald icon in the system tray area where you can change the rendering, etc. (use Xgl or AIGLX, etc)

---

### Post by Ubivetz on 2007-07-17
> **cyberdork33 said:**
> DISPLAY=:1 beryl-xgl

Don't do that.

start Xgl, start kde or gnome or whatever, then just do 
'beryl-manager' that is it. you do not need the script. You should get a emerald icon in the system tray area where you can change the rendering, etc. (use Xgl or AIGLX, etc)
Ok, the question is: why gnome & xgl works so slow, but whithout any DE Beryl works?

---

### Post by cyberdork33 on 2007-07-17
> **Ubivetz said:**
> Ok, the question is: why gnome & xgl works so slow, but whithout any DE Beryl works?

The whitescreen thing is a common result of a problem. There are SEVERAL webpages and threads about it, basically because it doesn't have a direct fix. Have you completely uninstalled beryl and tried starting your DE in XGL?

---

### Post by Ubivetz on 2007-07-17
> **cyberdork33 said:**
> The whitescreen thing is a common result of a problem. There are SEVERAL webpages and threads about it, basically because it doesn't have a direct fix. Have you completely uninstalled beryl and tried starting your DE in XGL?
i have beryl installed, but **not running**. Should I try to install XGL from sources in order to obtain newer version?

---

### Post by cyberdork33 on 2007-07-17
> **Ubivetz said:**
> i have beryl installed, but **not running**. Should I try to install XGL from sources in order to obtain newer version?

I understand that it is not running. I am trying to see what might be interfering or something. If you want to compile from source, go ahead, but I don't think there is a need to. The repos have what you need.

---

### Post by Ubivetz on 2007-07-18
> **cyberdork33 said:**
> I understand that it is not running. I am trying to see what might be interfering or something. If you want to compile from source, go ahead, but I don't think there is a need to. The repos have what you need.
It's pity. Could you show your /etc/X11/xorg.conf? If you use Mobility Radeon X1600 on iMac, it could be useful for me.

---

### Post by cyberdork33 on 2007-07-18
> **Ubivetz said:**
> It's pity. Could you show your /etc/X11/xorg.conf? If you use Mobility Radeon X1600 on iMac, it could be useful for me.

I actually don't have it setup right now as I was doing some gutsy testing, and have been using compiz-fusion recently anyway. Your xorg config looks ok... You could try running
```
ati-config --overlay-type=Xv
``` which appears to be missing...

Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=463791](http://ubuntuforums.org/showthread.php?t=463791)

---

### Post by Ubivetz on 2007-07-19
> **cyberdork33 said:**
> I actually don't have it setup right now as I was doing some gutsy testing, and have been using compiz-fusion recently anyway. Your xorg config looks ok... You could try running
```
ati-config --overlay-type=Xv
``` which appears to be missing...

Have you seen this thread?
[http://ubuntuforums.org/showthread.php?t=463791](http://ubuntuforums.org/showthread.php?t=463791)
I have tried 
```

aticonfig --overlay-type=Xv

```
with no result.

---

### Post by Levo75 on 2007-10-12
I don't know if my cpu is 64bit how can i check?

I currently have the 32bit version of feisty on my mac, the graphics and wifi seem the hardest to configure.

---

