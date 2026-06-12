---
title: "boot to safe graphics mode in linux"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by battleshipterry on 2008-01-28
when booting 7.10 on a usb drive how do I get into safe graphics mode (what key do you push Eg. f6 or f8 and when) I need to get to desktop, I dont care if it is low graphics, just need in to graphical desktop (not command prompt).when I boot this removable drive box with 7.10 umuntu on my laptop it fails after splash screen.but boot splash screen looks great.I dont want to change xorg because it works great on my desktop PC.

---

### Post by jpeddicord on 2008-01-28
There is no "safe graphics mode" - but the display should automatically fall back to a lower display if it can't start. Can you describe the exact problem you are having? What happens after the boot screen?

---

### Post by battleshipterry on 2008-01-28
Yea it boots the splash screen fine but after orange bar completes loading and it jumps to the command line screen it has [COLOR="DarkGreen"]ERROR Microcode "bcm43xx_microcode5.fw" not available or load failed Message [/COLOR]repetable popping up on screen.I am trying to fix a windoze lappy that has a possable virus and I wanted to use linux to boot on it.to grab files from lappy (it was not backed up and linux somewhat amune to virus's)but my removable drive will not boot on this lappy.I altered the xorg to get to run on my desktop PC that has a PCIe card that took a while. and would not want to mess up xorg to solve this problem.Thanks for any help.

---

### Post by macogw on 2008-01-28
Well the splash screen has nothing to do with xorg.  That's entirely done in the framebuffer, so it working means nothing regarding what will happen after it's done booting.  If your xorg.conf isn't set up to work with this comp, though, that'd be why you can't start x.  You can backup the current xorg.conf like this ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` then make your modifications for it to work on that computer.

---

### Post by battleshipterry on 2008-01-29
I ended up using slax live cd it booted to desktop fine thanks all for help.

---

