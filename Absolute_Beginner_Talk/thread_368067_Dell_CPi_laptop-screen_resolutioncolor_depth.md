---
title: "Dell CPi laptop-screen resolution/color depth"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by malt^ on 2007-02-22
Hello Everyone,
 Kinda newbie here (know enough to get me in trouble), just finished loading Ubuntu onto my Dell CPi laditude laptop (using "Neomagic NM2160 - Magicgraph 128XD") and having it updated to the latest kernel. (6.06 LTS)
 Now trying to get the screen reolution up to 1024x768.

Started with a Terminal screen and did this:
1.) sudo apt-get install hwinfo
2.) sudo hwinfo --framebuffer

and found my needed resolution to be 0x0317 (to obtain the 1024x768)
I then did this:
3.) sudo nano /boot/grub/menu.lst
and found this line of coding...

## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

I then did this to the line of code....
4.) # defoptions=quiet splash vga=0x0317

and then this...
5.) CTRL+O
6.) CTRL+X
7.) sudo update-grub

it asked if to over write existing code..I answered "yes"
it replied with....
### END DEBIAN AUTOMAGIC KERNELS LIST

                             [ Wrote 153 lines ]


now the part i'm stumped on...it won't set the resolution to this new coding after re-booting, so what am I doing wrong??

---

### Post by netkid91 on 2007-02-22
You're doing too much, you are only changing the res of the CLI, to change your GUI res go to System->Preferences->Screen Resolution.

---

### Post by malt^ on 2007-02-22
Well sadly that was the first thing I checked after installing Ubuntu, all the is available is the lower settings 800x600 and 640X480, the higher stuff isn't showing up at all.

---

### Post by netkid91 on 2007-02-22
You need to edit your Xorg.conf file:
sudo gedit /etc/X11/xorg.conf
From a terminal, once you find the screen section it should become obvious what to do.

---

### Post by malt^ on 2007-02-22
Netkid91 I'm a happy camper now :D You Rock!
I can actually see correctly and my next project will be the sound card, but its late, and I need to get some sleep to make money in the morning...have a good night and a beer on me ;)

---

### Post by netkid91 on 2007-02-22
Heh, thanks.  This is why I am here, if you ever need any help in the future feel free to PM me.

---

### Post by jesterjaimi on 2007-02-28
Well, I am using a Dell Latitude D420 Laptop with an Intel 945GM (GMA 950) Graphics Chip Set, and I have been thru the "sudo dpkg-reconfigure xserver-xorg" ritual a bunch of times now, but I can't get the 1280x800 screen resolution to show up in the resolution preferences. Got it working on the other Fedora Core Partition, but no dice on Ubuntu 6.06. Not a big deal. When compared to the install process I had to go thru for the first partition, this was very uneventful, which is nice. But now if I could figure out a way to get full screen resolution, I would be really psyched.

Thx in advance.

~jj

---

### Post by netkid91 on 2007-03-01
Jester, your post does not belong in this thread.  Please either post a new thread or preferably, use the search function, as I know this question has been answered many times before.

---

