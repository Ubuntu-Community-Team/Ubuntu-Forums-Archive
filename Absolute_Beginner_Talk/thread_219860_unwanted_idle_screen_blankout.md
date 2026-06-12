---
title: "unwanted idle screen blankout"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-07-20
when my computer goes idle, my screen goes black.

i've made sure the power management preferences aren't enabling this and i've disabled the screensaver as well.

am i missing something?

---

### Post by orb9220 on 2006-07-20
No I have and others trying to track this down. It seems that it is a mish mash of implementing something as DPMS and screensaver.

It DOES NOT matter what the gnome-power mangement says I have both on never.

If you open a term and enter: xset q you will see the state minse says

DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 2400
  DPMS is Disabled
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log

IF my DPMS is disabled then why is my monitor still blanking off?

Anybody?

And where are those numbers for Standby Suspend Off stored I looked thru the logs it says it using nothing there 

I'll get back to you if I can ONCE AND FOR ALL! find a solution. Since it keeps going back to those settings.

---

### Post by shanepardue on 2006-07-20
sheesh! i felt dumb asking it, but it seems like more of an issue than i thought. i figured it was something little i was just missing. 

well, let me know when you find a solution, it gets really lame watching a movie and having to move the mouse ever so often!

---

### Post by jcmachad on 2008-02-29
Anyone? I am having this same issue

---

### Post by Jennabob on 2008-03-01
yes I am having the same issue and it is driving me nuts! here is my xset q

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffdfffdfffef
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /home/jenna/.gnome2/share/cursor-fonts,/usr/share/fonts/X11/misc/,/usr/share/fonts/X11/Type1/,/usr/share/fonts/X11/100dpi/,/usr/share/fonts/X11/75dpi/,/home/jenna/.gnome2/share/fonts,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/,/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/fonts/,/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/oblique-fonts/
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Display is not capable of DPMS

---

