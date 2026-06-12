---
title: "Suspend/Resume, Headphones and IR remote on Karmic/MacBook pro 5.1"
date: 2009-11-21
forum: Apple Hardware Users
---

### Post by luigi.viggiano on 2009-11-21
If anybody is experiencing problems with Suspend/Resume , this can be solved adding **acpi=noirq **to kernel options in grub.

If headphone do not work, try installing gnome-alsamixer to unmute the headphone channel.

I still have the infra red remote control not working

See: [http://en.newinstance.it/2009/11/20/suspendresume-problem-in-ubuntu-karmic-910-running-on-macbook-pro-51/](http://en.newinstance.it/2009/11/20/suspendresume-problem-in-ubuntu-karmic-910-running-on-macbook-pro-51/)

---

### Post by ercoppa on 2009-11-21
For Ir remote see[ this]("https://help.ubuntu.com/community/MacBook5-1/Karmic#Remote Control").

Greets, ercoppa.

---

### Post by luigi.viggiano on 2009-11-21
it doesn't work for me, i'll try again, maybe i missed something.

Also I get strange colors in video playback (vlc, totem) it seems that hue saturation is wrong, I see everything blue. when I open nvidia-settings, then the hue saturation go fine, but after if I restart vlc/totem, I get back wrong colors... nobody is having same issue?

---

### Post by cyphaw on 2009-11-26
I had the same for the hue, I had to change the settings in totem itself, the hue cursor was completely on the left. Try it.

cyphaw

---

### Post by luigi.viggiano on 2009-11-26
Yes, thanks, I got to the same conclusion some days ago. I forgot to post the solution, but hopefully your answer will help other guys with same problem.

---

### Post by namethatmeetsstandards on 2009-12-07
I tried this for a macbook pro 4,1. It doesn't resolve the problem. 
The pm-suspend logfile says all goes well, but I keep having the cursor flickering in the upper left corner of a black screen. And no interaction is possible anymore: I have to hard-reboot.

_________________last lines of pm-suspend.log___________________
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
Sun Dec  6 17:32:50 CET 2009: performing suspend


Does anybody have more suggestions? I've tried to toggle both these options in /etc/pm/config.d/00sleep_module
#SLEEP_MODULE="uswsusp"
#SUSPEND_MODULES="sky2"

but no results.

If anybody has some idea how to debug this, I'd be greatful!

---

