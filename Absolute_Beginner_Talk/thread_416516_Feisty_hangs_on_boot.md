---
title: "Feisty hangs on boot"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-04-21
I upgraded from edgy to feisty and all i've had are problems. Booting hangs after * Running local boot scripts (/etc/rc.local) [OK]" Whats happening?

---

### Post by johnny4north on 2007-04-21
others are having same problem - [http://ubuntuforums.org/showthread.php?t=415756&highlight=Running+local+boot+scripts](http://ubuntuforums.org/showthread.php?t=415756&highlight=Running+local+boot+scripts)
skip and dave
We'll need to know exactly what your kernel is saying so we can identify the problem. Where is it crashing? Does it enter X? Two things:

1) Boot in recovery mode. You will NOT see a splash screen and the kernel will be outputting information verbosely. Are there any problems? If it does crash at this point, what kind of error message does it give you? Perhaps save a copy of /var/log/messages and post it? Could you output the contents of 'dmesg' to a file and post that as well? You can access these files if you boot up Ubuntu through a LiveCD. Mount the drive containing your Ubuntu installation and you'll have access to the entire drive.

2) If it does get past booting and goes into X, it's likely not a startup issue (unless its something subtle, like a driver/module problem). What does your /var/log/Xorg.0.log say? Do you have an Xorg.20.log too? Make sure that your /etc/X11/xorg.conf file is loading the correct video driver! Try using the 'vesa' driver instead of 'nvidia' or whatever it was you were using. If this solves it, you'll need to recompile the driver for your video card (highly recommended) or you could download another one through synaptic via the restricted modules package.
Reply With Quote

How to boot in recovery mode:

Turn on your computer. Before Ubuntu begins to start up, you will see a quick message saying something like:
Quote:
GRUB loading
Hit "ESC" to enter the GRUB menu.
There will be a three second timer. Before that time runs out, you have to hit Escape. You will be brought to a menu. Use the up and down keys to select an option that says "recovery mode" and hit enter.

---

### Post by goodbyewindows on 2007-04-21
> **johnny4north said:**
> others are having same problem - [http://ubuntuforums.org/showthread.php?t=415756&highlight=Running+local+boot+scripts](http://ubuntuforums.org/showthread.php?t=415756&highlight=Running+local+boot+scripts)
skip and dave
We'll need to know exactly what your kernel is saying so we can identify the problem. Where is it crashing? Does it enter X? Two things:

1) Boot in recovery mode. You will NOT see a splash screen and the kernel will be outputting information verbosely. Are there any problems? If it does crash at this point, what kind of error message does it give you? Perhaps save a copy of /var/log/messages and post it? Could you output the contents of 'dmesg' to a file and post that as well? You can access these files if you boot up Ubuntu through a LiveCD. Mount the drive containing your Ubuntu installation and you'll have access to the entire drive.

2) If it does get past booting and goes into X, it's likely not a startup issue (unless its something subtle, like a driver/module problem). What does your /var/log/Xorg.0.log say? Do you have an Xorg.20.log too? Make sure that your /etc/X11/xorg.conf file is loading the correct video driver! Try using the 'vesa' driver instead of 'nvidia' or whatever it was you were using. If this solves it, you'll need to recompile the driver for your video card (highly recommended) or you could download another one through synaptic via the restricted modules package.
Reply With Quote

How to boot in recovery mode:

Turn on your computer. Before Ubuntu begins to start up, you will see a quick message saying something like:
Quote:
GRUB loading
Hit "ESC" to enter the GRUB menu.
There will be a three second timer. Before that time runs out, you have to hit Escape. You will be brought to a menu. Use the up and down keys to select an option that says "recovery mode" and hit enter.

1) No errors in recovery mode, it hangs yet again after running local boot scripts. The screen goes black but if I press ctrl-alt-F1, I can get back to command line. It's hard to copy the files to you because my wireless usb adapter for the laptop isn't working.
2) Vesa worked!!, thank you so much! How to I recompile it?

edit: no wait, vesa worked once. now same error!

---

### Post by johnny4north on 2007-04-21
when, you make in back in with vesa driver.  check your restricted drivers. panel > system > administrator > restricted drivers managers, then enable. i hope it works for you. :)   i got get some shut-eye. cya later

---

