---
title: "Screen Saver"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Imsati on 2006-09-27
My screen saver won't activate when it should--won't activate at all actually.

Everything tests fine, set to start after 10 minutes, Tested it and it works flawlessyly.

4 hours go by, and nothing.

Thoughts?

TIA!

---

### Post by orb9220 on 2006-09-27
> 4 hours go by, and nothing.

What apps do you have running. Some apps will or can be set to disable screensaver.

In a terminal type
xset -q

Then copy and past results here.

---

### Post by Imsati on 2006-09-27
Orb,

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  250    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfe5ef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Disabled
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

---

### Post by Imsati on 2006-09-27
I just locked my session on a whim and the screen saver appeared as soon as I did so, so I know the settings took effect.

---

### Post by CatKiller on 2006-09-28
Just a quick question, is the "Activate screensaver when session is idle" checkbox ticked?

---

### Post by Imsati on 2006-09-28
WEll, I'm using Kubuntu, so that would translate to what exactly?

It's set to start after 5 minutes of inactivity.

---

### Post by CatKiller on 2006-09-28
I have no idea. I haven't used Kubuntu. It was just a quick sanity check, since with gnome-screensaver it's possible to set the time without actually turning it on.

---

### Post by handleyj on 2006-10-01
I'm having this exact same problem.  Set the screen saver in Kubuntu, and it just never comes on.

I installed Ubuntu, then did an apt-get of kubuntu-desktop.

Anyone have a suggestion?

Thanks!

-joe

---

### Post by handleyj on 2006-10-01
Right...known bug in KDE 3.5.3:

[http://www.ubuntuforums.org/showthread.php?t=199381](http://www.ubuntuforums.org/showthread.php?t=199381)

---

