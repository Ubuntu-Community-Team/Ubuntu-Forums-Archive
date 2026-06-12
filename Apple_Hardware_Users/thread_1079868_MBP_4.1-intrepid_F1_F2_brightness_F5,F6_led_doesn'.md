---
title: "MBP 4.1-intrepid F1 F2 brightness F5,F6 led doesn't work"
date: 2009-02-24
forum: Apple Hardware Users
---

### Post by sashimee on 2009-02-24
Hello.

I've installed intrepid on MBP 4.1 along with s/w from mactel-support(hal-applemc and etc)

However, F1,F2 key (LCD brightness control) and F5,F6 key(keyboard led control) doesn't work. The sound control(F10~F12) works fine though.

What could I have done wrong?

Thank you.

p.s. please don't direct me to this link [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid)

---

### Post by chort27 on 2009-02-24
> **sashimee said:**
> Hello.

I've installed intrepid on MBP 4.1 along with s/w from mactel-support(hal-applemc and etc)

However, F1,F2 key (LCD brightness control) and F5,F6 key(keyboard led control) doesn't work. The sound control(F10~F12) works fine though.

What could I have done wrong?

Thank you.

p.s. please don't direct me to this link [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid)

i don't think there is brightness control on ubuntu... if I am wrong I would go into your settings>>hotkeys and try to assign it to those originals

---

### Post by sashimee on 2009-02-24
I've seen postings that ppl are using F1,F2 keys just as F10~F12 keys are used exactly same in mac to control sound.

---

### Post by sashimee on 2009-02-24
In Systems Keyboard setting, Layouts tab,

Keyboard Model was previously set to generic

I've changed this to MacBook/MacBrook Pro(Intl) and got the following error pop up:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10502000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Could this be what's causing the problem??

---

### Post by cyberdork33 on 2009-02-24
you might also need to install the gnome-power-manager from the mactel PPA.

---

### Post by sashimee on 2009-02-25
dude I already installed gnome power manager and it has nothing to do with F1 F2 keys not working.

---

### Post by buntuLo on 2009-02-25
> **sashimee said:**
> dude I already installed gnome power manager and it has nothing to do with F1 F2 keys not working.

Sashimee, please check that you have installed the version from the Mactel PPA, as suggested by Cyberdork. it has a lot to do with display brightness control, it's exactly the issue that has been addressed in that version.
for me, display brightness works with the standard KDE power manager. when you have it working from there, it's just a matter of mapping the desired hotkeys.
by the way, if the standard hotkeys do not work, try mapping it to some other keys.. it might help: i don't know for you, but here on MBP5,1 keyboard layout is quite messy and i got it working only assigning them to << and >> (player backward and forward).

---

### Post by sashimee on 2009-02-25
I did sudo apt-get update and then sudo apt-get install gnome-power-manager.

It saids gnome-power-manager is already the newest version.

Should I delete this gnome power manager and install again?

sorry I'm a linux noob, how do I delete this?

Thank you.

---

### Post by cyberdork33 on 2009-02-25
> **sashimee said:**
> I did sudo apt-get update and then sudo apt-get install gnome-power-manager.

It saids gnome-power-manager is already the newest version.

Should I delete this gnome power manager and install again?

sorry I'm a linux noob, how do I delete this?

Thank you.
so did you add the mactel ppa to your sources?

---

### Post by sashimee on 2009-02-25
yes 
I DID include the mactel support in the sources earlier.
I couldn't have installed hal-applemc and etc if I didn't.

Any ideas?

---

### Post by cyberdork33 on 2009-02-25
you can check the version of gnome-power-manager you have with:
```
aptitude show gnome-power-manager
```

---

### Post by deltaiscain on 2009-02-27
did you add mbp_nvidia_bl to etc/modules? and add applesmc too, to etc/modules. 
open terminal, type sudo nautilus, enter password, go to file system, then folder etc, then sources file. open it, at bottom add mbp_nvidia_bl and under that applesmc. save, restart, and hope it works now. And did you install the latest gnome power manager? 2.24 i believe?

---

### Post by sashimee on 2009-02-27
Now it works!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

For those of you with MBP 4.1 - intrepid,

if you backlight, keyboard led doesn't work with F1~F6 keys

edit your /etc/modules and add applesmc

---

