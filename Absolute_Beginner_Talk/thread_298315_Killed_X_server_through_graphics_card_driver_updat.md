---
title: "Killed X server through graphics card driver update"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by daverave999 on 2006-11-12
Hi folks.
I'm about a week into my first ever desktop install of anything other than Windows, and until now everything has been going incredibly well. I've not even booted back into Windows yet as everything I've needed I've managed to sort out.

Unfortunately, I've hit a stumbling block. Earlier, I installed the nvidia drivers from the nvidia website (1.0 9xxx something). I already had the ones installed through Synaptic, 1.0 7xxx something.
 IIRC, I switched to a console (Ctrl+Alt+F1) and did ```
/etc/init.d/gdm stop
``` then tried ```
rmmod nvidia
```which didn't work, saying that it was not found. (Either of those may have had sudo in front of them, can't remember tbh). Stupidly, I continued to install the new driver at this point, which worked fine.

The problem comes when I restart my machine, and I get an error message saying something like "x server cannot be started" because xorg.conf says that the nvidia driver is the 7xxx version and this conflicts with the 9xxx one that is actually installed. I open /etc/X11/xorg.conf in vi/vim but there is no mention of any version in there that I can alter.

If anyone has any suggestions I will be most grateful. Apologies for the vagueness of bits and pieces but I'm currently on my brother's PC as I can't boot into a windowed system!

[EDIT] This is on Edgy btw.

---

### Post by woedend on 2006-11-12
ok, do you still have the shell script(the .RUN file that installs nvidia from the website?).
if so, issue the command:
./NAMEOFINSTALLER --uninstall
then I would reinstall the version from the repos(nvidia-glx).
If you want the 9 series to work, i'd remove the nvidia-glx package, blacklist the nv module(as outlines in the huge howto), then install the 9x series again

---

### Post by daverave999 on 2006-11-12
Thank you very much for your reply!

I didn't know what the uninstall command would be. I uninstalled it, then tried restarting gdm, no luck. So I rebooted, still no luck. I had hoped the generic driver, or whatever was on there before I installed the 9629 driver would work but it didn't and I couldn't remember how to install anything else other than this driver (as I still had it on the desktop).

So I went through the steps I did last time, and the rmmod nvidia worked this time. No idea why it did as opposed to last time, but it worked. So here I am back in Gnome, with the latest drivers.

Thanks again woedend, I'd still be stuck at the command line without your help!

---

