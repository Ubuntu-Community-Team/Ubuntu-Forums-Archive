---
title: "Three different sound options, sant to disable two of them"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by rfaith88 on 2008-02-29
I have three options for sound:  HDA Intel, CA0106, and SIgmaTel

The only one that works for me (which is where my speakers are plugged in) is the CA0106.  I want to disable or get rid of the other two, so that my sound works when I start up my system.  Is there a way to do that?  or at least set one as the default?

---

### Post by Iandefor on 2008-03-01
You have a couple of options.

You could try setting the CA0106 as the default output in the Sound configuration dialog (System->Preferences->Sound). 

If that doesn't work, which it might not, speaking from experience using a system with multiple sound cards, you could also try blacklisting the kernel modules for the two cards you don't want.

Here's how to go about doing that: do
```
gksudo gedit /etc/modprobe.d/blacklist
``` Add "blacklist [module name]" to the end of the file, and do that for as many modules as you have to, save, and reboot.

Working out the module names (if you don't already know them) shouldn't be a challenge; they're usually not too different to what they're called in any of the sound configuration dialogs. Just look for similarities between the names of the other two cards and the output of the command ```
lsmod | grep snd
```

---

