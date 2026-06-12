---
title: "desktop won't load"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by yogurtboy on 2007-08-11
i just installed Ubuntu on a relative's crappy PC. it has an older monitor, probably 17"

when i took her tower, all i did was unplug everything, and took the tower to my house

i plugged all MY peripherals in - including a larger 21" monitor, capable of higher resolutions.

i installed ubuntu, set up a non-root user account, copied her files, etc... everything went fine

today i unplugged all my stuff, brought the tower back to her place, plugged everything in (including her smaller/lower res monitor), and booted up

boot-up started fine, and the Ubuntu progress bar displayed, and none of the things loading read 'error'. Things went fine UNTIL the login screen tried to display (just before the desktop would have loaded). at this point the monitor went black - nothing.

i suspect the system was trying to load a screen size/resolution on a monitor incapable of handling the size/res.

does this seem reasonable? if so, what's the workaround?

i tried booting with the Live CD and it loaded fine

I also booted from the HDD in "safe" mode [or whatever it's called], and got to the command line, and confirmed the file system is intact. however, i'm not much of a command line guy, so aside form "cd" and "ls" there wasn't much else i could [to try to load GUI mode, for example]

in short, i don't think there's a hardware ERROR, just some configuration that needs to be done, but i'm in a catch-22 situation

i suppose i could haul my heavy monitor over there and lower the resolution, shutdown, and reboot.

but is there a more elegant solution?

or do i have a bigger problem?

thanks in advance, 
steve

---

### Post by kronk on 2007-08-11
What's the graphics card Steve ?

---

### Post by yogurtboy on 2007-08-11
not exactly sure which graphics card it is - it's built into the MoBo

from running the memory test BEFORE installing ubuntu, i seem to recall "SiS 730" as the chipset

---

### Post by kronk on 2007-08-11
I'm no guru but I've had simular problems before and it sounds very much like as you suggest a graphics mode above the capability of the "new" ;) monitor.

You might get away with "sudo dpkg-reconfigure -phigh xserver-xorg"

If not you could get the shell up and edit your /etc/X11/xorg.conf file.

Try that command first as I "think" it'll reset your variables to a lower base setting.

---

### Post by yogurtboy on 2007-08-11
ah, worked like a charm!

the single command, "sudo dpkg-reconfigure -phigh xserver-xorg" was all that was needed

many thanks kronk!

---

