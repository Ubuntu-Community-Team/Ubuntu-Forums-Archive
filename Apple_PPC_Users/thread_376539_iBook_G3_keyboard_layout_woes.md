---
title: "iBook G3 keyboard layout woes"
date: 2007-03-05
forum: Apple PPC Users
---

### Post by bostoys on 2007-03-05
Hi guys,

I'm using an iBook G3 and ubuntu version 6.06. I have been trying all night to get Linux to work with my laptop keyboard (the two Apple "super keys" don't do anything.). I've messed with the xmodmap files, messed with all kinds of things. All I want is for the two apple keys to act as command keys, just like they do in Mac OS. Also, I want the ctrl key on this keyboard to bring up the context menu if I hold it down and click the mouse. 

Also, less importantly, I'd like the top row of the keyboard (brightness, volume, eject) to do what they're meant to do, and to only act as Fn keys when i hold down the Fn key on the keyboard...I wonder if anyone can help! Thanks so much.

---

### Post by maggot_brain on 2007-03-05
I tried Ubuntu 6.10 on an iBook G3 and had similar problems to you including there being broken Macintosh keyboard layouts in X.  I'm currently running Debian Etch which works fine.  I've tested Feisty Herd 4 and some of the problems appear to have been fixed.  I would recommend either using Debian or waiting for Feisty to be released.

---

### Post by meathook on 2007-03-07
i'm on a g4 but had similar preferences on my keyboard behavior. i searched the net and found the following to resolve those issues:

mouseemu lets you do ctrl+left click to bring up context menus. i found it in the repositories. sometimes there's a lag or a short freeze. i'm not sure if it's mouseemu or something else causing it but most of the times it works. 

for the brightness and volume things, there's pbbuttonsd. it was already installed by default though. so if you press fn + f3, it toggles mute.

---

### Post by bostoys on 2007-03-08
hey. thanks a lot for those tips. only one more thing- how can i make Apple act as Control?

---

### Post by trash on 2007-03-09
i´ve discovered you can type ´eject´ in a terminal to pop the cd tray.

---

### Post by mhinton539 on 2007-03-17
My iBook G3 (an old Clamshell iBook SE, 366 MHz) ran quite well with Kubuntu 6.06 LTS. But I've just installed Ubuntu 6.10 (Edgy), and have a number of keyboard and display issues. My Function keys have been working quite well, as have the Apple/Command keys. But for some reason, the Shift key has been non-functional (and I was getting tired of "toggling" the caps lock, and being unable to enter an asterisk, etc). Rebooted several times, after trying a number of keyboard mappings; no luck. Just shut down, left for a few hours and came back: Now the Shift is working fine. No idea if it will still be working if I reboot again -- may be something in the hardware detection/probing at boot...

As for the function keys, I can change brightness and see the resulting mini-box telling me where the brightness is set...but the backlight intensity never changes. Hmmm...

My suggestion would be to try 6.06 LTS; it didn't seem to have these problems.

--mark

> **bostoys said:**
> Hi guys,

I'm using an iBook G3 and ubuntu version 6.06. I have been trying all night to get Linux to work with my laptop keyboard (the two Apple "super keys" don't do anything.). I've messed with the xmodmap files, messed with all kinds of things. All I want is for the two apple keys to act as command keys, just like they do in Mac OS. Also, I want the ctrl key on this keyboard to bring up the context menu if I hold it down and click the mouse. 

Also, less importantly, I'd like the top row of the keyboard (brightness, volume, eject) to do what they're meant to do, and to only act as Fn keys when i hold down the Fn key on the keyboard...I wonder if anyone can help! Thanks so much.

---

