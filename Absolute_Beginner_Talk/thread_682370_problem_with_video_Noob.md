---
title: "problem with video Noob"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by never_retreat on 2008-01-29
I'm running 7.1, I going to try to explain this the best i can. I was in the drivers tab (?) and was checking out the video driver. It said something about a different driver for the video card. It had a check box to use the other available something. So i checked it, prompted for reboot, ok why the hell why not. BIG mistake. The computer starts and I get as far as the ubuntu loading screen thing and then it goes blank.
Is there some sort of safe mode boot like winblows has so I fix this problem? HELP And please keep responses very dumb because this is my first linux experience.

---

### Post by jaytek13 on 2008-01-30
What video card are you using?

---

### Post by never_retreat on 2008-01-30
ATI radeon x1600 pro
Gecube

---

### Post by never_retreat on 2008-01-30
bump

---

### Post by oedha on 2008-01-30
you have to go to console mode
ctrl+alt+F2
fill username and password
you can do :==> sudo dpkg-reconfigure xserver-xorg
or sudo dpkg-reconfigure -phigh xserver-xorg

~E~

---

### Post by never_retreat on 2008-01-31
No dice
I can hit ctr alt f2 during the ubuntu boot banner thing and see the boot sequence, but after that the screen still goes blank.

---

### Post by jaytek13 on 2008-01-31
When you boot up your computer, after the BIOS screen the GRUB boot loader will give you about 3 seconds where you can press escape. So, you press escape and it will bring up some other options. One of those options should be a "recovery mode." If there's more than 1 recovery mode select the one for the most recent kernel. The recovery mode will boot up the command line and allow you to run the commands posted earlier.

---

### Post by njparton on 2008-01-31
You need to edit your /etc/X11/xorg.conf file and do 2 things:

change the line that refers to the driver module back to "vesa". For nvidia cards this will read "nv" or "nvidia", I've never used ATI/AMD graphics so I imagine you're looking for the line that reads "ati" or "amd".

Also, comment out the block that refers to "glx" using "#" symbols.

Then reboot.

If you want to try again, install envy and use that (google it).

---

