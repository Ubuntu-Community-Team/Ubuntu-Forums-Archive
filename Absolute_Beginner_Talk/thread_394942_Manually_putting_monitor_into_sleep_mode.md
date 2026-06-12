---
title: "Manually putting monitor into sleep mode"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by rangi500 on 2007-03-27
Hi guys,

In Ubuntu, Is it possible to manually put the monitor into sleep mode, for example, by pressing a key combination or moving the mouse to a corner of the screen? I've seen this done on both Windows and Mac, but not sure how to on Ubuntu (running Gnome).

I'm embarrassed to say my reason for this question is laziness - I want to be able to put the monitor into sleep mode straight away after watching movies/tv on my computer, without having to get out of bed and switch off the monitor!

Any help much appreciated!

Thanks,
Rangi

---

### Post by marios88 on 2007-03-29
I actually have a similar problem to yours,

My screen wont go to sleep and the lcd backlight stays on it would be convinient to manually sleep it before leaving...

(Fujitsu Siemens Amilo PA1510)

---

### Post by oilchangeguy on 2007-03-29
try system, preferences, power management. adjust the slider bar to your desired time.

---

### Post by kerry_s on 2007-03-29
You can create a launcher/icon with " xset +dpms dpms force off " as the command.

+dpms <- turns the auto off timer back on
dpms force off <- turns the screen off immediately

---

### Post by kerry_s on 2007-03-29
> **oilchangeguy said:**
> try system, preferences, power management. adjust the slider bar to your desired time.

The problem is if you use a media player it disables the power settings so the screen doesn't turn off while playing movies, it does not turn it back on on it's own. You can try it and use xset -q in terminal to view the settings.

---

### Post by rangi500 on 2007-03-29
Kerry thanks very much for taking the time to reply, your suggestion works like a charm.

Thanks!
Rangi

---

### Post by rangi500 on 2007-03-29
By the way, I created a keyboard shortcut for doing this by following this short guide:

[http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/)

(in case anyone's trying to do the same as me)

---

### Post by marios88 on 2007-03-30
> **kerry_s said:**
> You can create a launcher/icon with " xset +dpms dpms force off " as the command.

+dpms <- turns the auto off timer back on
dpms force off <- turns the screen off immediately


Your code worked like a charm thank you very much :guitar: 


Is there any way to manually set the dpms off after some time?

I read the man pages but i didnt get it....

```

DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```


Edit: 

Ok i found the code

xset dpms 300 600 900

If your display is not going normaly to sleep as mine try this(numbers are in seconds)

---

