---
title: "Help Needed: Kubuntu Feisty Fawn Install"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by TwoEdgeXtreme on 2007-05-24
My Computer: 
HP Pavillion dv6105us
Trying To Install:
kubuntu feisty fawn 7.04

It boots to live cd fine the video is perfect installs op with only one hitch @ the end
When it says you must reboot your system now or continue with live cd, i click reboot, it begins to terminate applications, ejects cd, and states press enter to continue
when i press enter it hangs and does nothing, so i force a power cycle to restart the computer.
Then it boots grub and displays a loading splash screen, and when it comes to the point where a log in screen should be it shows me a blank screen and hangs.

I am trying to learn linix and I know everyone has already heard this before but I am wet behind the ears when it comes to utilizing alternative operating systems such as this. Any help with this issue would be most appreciated!

---

### Post by Sparkster185 on 2007-05-24
If you manually close the CD-ROM drive (press the button on it) and then hit ENTER, does that work?  I've install Kubuntu on three machines and never had anything like this happen.

Maybe you just need to be more patient after you hit ENTER?

---

### Post by Happy_Man on 2007-05-24
Did you burn the CD at the lowest speed possible? Did you check it for defects before installing from it?

---

### Post by jerrylamos on 2007-05-24
From your description, install worked but the restart didn't.  There are some Feisty bugs in this area depending on the hardware configuration.  This computer in particular fails on shutdown and needed a workaround.

There are also some difficulties in the screen support.  A number of people have been able to proceed with symptoms similar to what you have by getting up to the blank screen and doing:
Ctrl-Alt-F1
Hopefully you'll get a command line screen.  If so, take a look at any messages there may be and if you think they are noteworthy, post them to your thread.

A typical case is the Xwindows code for starting the screen got into a race condition with some other part of boot, all of which is time and configuration dependent and more prevalent on Feisty which speeds up boot by doing several functions in parallel.

If you did get a command line, then do the following noting carefully no blanks before the - except for the -phigh
sudo dpkg-reconfigure -phigh xserver-xorg
enter your password
You should get a bunch of menus to select whichever graphics driver you'd like to try.  VESA is possible choice  (and slow) for many graphics chips.  It should also ask for screen resolution so you'll need to know that.

I don't have an HP to know what graphics chip it uses; does it display that on the Bios printout when you power on?

Cheers, Jerry

---

### Post by jucal on 2007-06-02
the problem is the driver navidia video vs kernel, is necesary that you edit the boot line in bgrub  and edit the kernel line add vga=792 or 789,

after is necesary change the driver video.

in spanish

soy hispanoparlante debes editar la linea de boot del kernel y adicional el parametro vga=792




Jucal

---

### Post by jucal on 2007-06-02
> **TwoEdgeXtreme said:**
> My Computer: 
HP Pavillion dv6105us
Trying To Install:
kubuntu feisty fawn 7.04

It boots to live cd fine the video is perfect installs op with only one hitch @ the end
When it says you must reboot your system now or continue with live cd, i click reboot, it begins to terminate applications, ejects cd, and states press enter to continue
when i press enter it hangs and does nothing, so i force a power cycle to restart the computer.
Then it boots grub and displays a loading splash screen, and when it comes to the point where a log in screen should be it shows me a blank screen and hangs.

I am trying to learn linix and I know everyone has already heard this before but I am wet behind the ears when it comes to utilizing alternative operating systems such as this. Any help with this issue would be most appreciated!

the problem is the driver navidia video vs kernel, is necesary that you edit the boot line in bgrub and edit the kernel line add vga=792 or 789,

after is necesary change the driver video.

in spanish

soy hispanoparlante debes editar la linea de boot del kernel y adicional el parametro vga=792




Jucal

---

