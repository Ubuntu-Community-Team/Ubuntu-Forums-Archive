---
title: "Installation problems"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by josh1892 on 2008-03-17
Hello.  I'm kind of new to ubuntu and have been having a near constant barrage of problems getting Ubuntu 7.10 Gutsy Gibbon to install.  I easily meet every system requirement and the actual installation wouldn't be a problem if I could even load the disc.

When I boot to the option menu before ubuntu tries to load, I have ZERO control over what I can do.  I can't even try to load it into the non-GUI version.  It eventually starts to load the GUI but then the left screen goes blank with a thin line at the top and the right screen gets these weird vertical lines that take up the most of the screen.  I know that it has loaded because I can go into the full page command lines interface.  I have tried every possible video fix I can think of, but my best guess is that it is an Nvidia video card problem.  Stupidly enough, Dell didn't think to use a normal motherboard and has no onboard video option, or else I would have tried that by now.  I have installed ubuntu into a virtual machine before and had no problems.  If I can get some help to get this video problem solved, I would be much obliged and will finally be able to get started using ubuntu.

System Specs
2005 Dell XPS400
Nvidia GeForce 6600
1 - DVI monitor (left)
1 - VGA monitor (right)
Logitech S510 Keyboard & Mouse combo

If you need any more information, ask and I'll try to assist you in any way possible.

---

### Post by uberlube on 2008-03-17
Try using only one monitor when booting and see if that helps.

---

### Post by josh1892 on 2008-03-20
i actually tried that with both of the monitors and i still got the same result.

i also tried to boot into a Gparted Live CD and i got the same thing, only, the left monitor was red instead of black.

---

### Post by uberlube on 2008-03-20
Do you have control in GRUB?

---

### Post by uberlube on 2008-03-20
And if you do, have you tried adding anything to the boot process to make it recognize your resolution?

---

### Post by josh1892 on 2008-03-20
no.  once the initial page for your boot options (boot the live cd or boot in safe graphics mode for instance) comes up i have no keyboard control.

---

### Post by Jimmyfj on 2008-03-20
The easiest way around the problems you describe during install is for you to download the alternate install cd from ubuntu.com. Go to the download section and simply markup the check box saying: Click here to download the alternate install cd. This install is non-GUI and very fast and stable yet still easy to run. 

Make sure that only one of your monitors are connected to the system during install. Dual monitor takes a few workarounds once the system is installed. You can find tons of threads about dual monitor on this forum later on, after install success.

---

### Post by uberlube on 2008-03-20
If you are getting a red screen and no keyboard, Im leaning towards a hardware problem. Make sure that everything is kosher in your BIOS. Other than that I couldnt really tell you what to do without physically being able to look at your system. Sorry.

---

### Post by josh1892 on 2008-03-20
that's the thing, though.  everything but the live cd works, or rather everything but the live cd GUI.  i've tried two different keyboards, swapping the monitors, and (as i said in the first post) i can go into the full page CLI.  i know it's not a hardware problem because i boot windows and everything else just fine.  i'm gonna try the alternate live cd after i finish downloading it and i can repartition the HDD.

---

### Post by allanE on 2008-04-06
I have the same problem on my XPS400. The keyboard  (usb) is not recognized after the live cd starts to boot. If you find a solution to this please post

---

