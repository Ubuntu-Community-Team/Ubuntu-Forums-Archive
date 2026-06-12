---
title: "[SOLVED] Can't save xorg.conf between reboots"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by schmildo on 2007-12-04
LOL here we go...
I'm not a complete noob, (well sort of) but the question deserved the entry here.
I'm just trying to save my xorg.conf file.

I've been using 'vi' for years.
I'm running Xubuntu 7.10
I can save the file no worries, and confirm the changes have been made after i've closed the file with 'view' or whatever. Hell, i've even used 'mousepad' GUI to confirm.

But If i reboot, the changes are gone.

Now I should warn you that I got tricky and installed it onto a USB stick. I'm not running off the HDD or a live cd. It was technically a live CD install onto the usb with a persistent partition however, (which I believe could be the problem)

I might need to move this thread, but I just wanted to check here first.

(geeze the things we do to install compiz)

---

### Post by Dr Small on 2007-12-04
> **schmildo said:**
> LOL here we go...
I'm not a complete noob, (well sort of) but the question deserved the entry here.
I'm just trying to save my xorg.conf file.

I've been using 'vi' for years.
I'm running Xubuntu 7.10
I can save the file no worries, and confirm the changes have been made after i've closed the file with 'view' or whatever. Hell, i've even used 'mousepad' GUI to confirm.

But If i reboot, the changes are gone.

Now I should warn you that I got tricky and installed it onto a USB stick. I'm not running off the HDD or a live cd. It was technically a live CD install onto the usb with a persistent partition however, (which I believe could be the problem)

I might need to move this thread, but I just wanted to check here first.

(geeze the things we do to install compiz)
Did you try editing the file with sudo ? xorg.conf is owned by root.

---

### Post by schmildo on 2007-12-04
yeah.

sudo vi xorg.conf

It seems to be making backups when i restart, those backups it's making do contain my changes.
I think some program is getting in, noting a change between it's local copy and xorg.conf, and restoring the file. I bet it has something to do with the apps in the gui that allow you to change the screen resolution and that kind of stuff.

and yeah , i'm certain i'm saving it, because i can close it and open it in another app with the saved changed,.... but when i reboot....

---

### Post by schmildo on 2007-12-05
behold! and answer has surfaced. (not the best answer but one to get me going)

I was trying to change the 'driver' setting under the 'device' section, but i've discovered that
the app called 'aticonfig' has the option to do this for me. It had the specific option to change what I waanted. It seems i have to use aticonfig because I have an ATI videocard.

Thanks for your help.

---

