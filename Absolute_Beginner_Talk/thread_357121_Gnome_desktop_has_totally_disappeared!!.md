---
title: "Gnome desktop has totally disappeared!!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-09
Up until now, I've never used any network capability under Ubuntu - although I regularly have my PC networked to my laptop under Windows.

This morning, I was booted into Windows and transferring some files between both machines. Then I needed to boot my desktop PC into Ubuntu and I happened to leave my laptop switched on. When Ubuntu booted, I got my login screen as normal - but after typing in my name & password, I'm just left with a blank orange screen. No desktop wallpaper, no icons, no menu bar - nothing!! It doesn't matter if I boot up as me or as root.

I've tried unplugging the network cable and rebooting but that doesn't fix it. What can have gone wrong?? :confused:

---

### Post by az on 2007-02-09
Whatever happened has nothing to do with you being networked.

Can you boot into recovery mode?

Had you done any updates?  Had you installed any new software previously?

---

### Post by John E on 2007-02-09
Thanks for the prompt response....
> **az said:**
> Can you boot into recovery mode?
Yes - but if I press CTRL+D at the end (to log in graphically) I get exactly the same problem (completely blank desktop).

> **az said:**
> Had you done any updates?  Had you installed any new software previously?The last update I did was yesterday morning when I did **apt-get install alsa-tools-gui** but it's been working fine since then. In fact, it was working fine this morning until I left that network connection powered up.

---

### Post by az on 2007-02-09
> **John E said:**
> Thanks for the prompt response....

Yes - but if I press CTRL+D at the end (to log in graphically) I get exactly the same problem (completely blank desktop).


Are we talking about recoverymode from grub or gnome-failsafe?

---

### Post by John E on 2007-02-09
Recovery mode from Grub. Sorry, but as it happens, I'd only backed up the partition last night so it seemed sensible just to restore my backup (i.e. it's now working again).

However, after restoring, I realised that what I wasn't seeing was the little applet that launches all my startup apps (it has an Ubuntu logo at the RHS and it progressively loads up various icons for FireStarter or whatever). Presumably it loads the desktop too.

I'd be interested to have your thoughts though, in case this happens again.

---

### Post by GrumpySmurf on 2007-02-14
I had something that sounds similar to this John E. I posted to another bloke's thread about it [here](http://www.ubuntuforums.org/showthread.php?p=2158463#post2158463).

I dont know if alsa-tools-gui is the real culprit, but it seems to have resolved the "blank desktop" problem I was having.

---

### Post by John E on 2007-02-16
Thanks GrumpySmurf - it looks like alsa-tools-gui might have benefitted from a bit more testing!! :)

---

