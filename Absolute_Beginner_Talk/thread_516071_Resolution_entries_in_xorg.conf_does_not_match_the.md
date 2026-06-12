---
title: "Resolution entries in xorg.conf does not match the GUI"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-08-02
I have a X850XT and installed it with Envy. All it did was to add some lower resolution options in the GUI, but none higher. Google Earth still runs like crap so full support doesn't seem to be enable anyways.

When I open xorg.conf, the entries under Screen, only have "1024x768" "800x600" "640x480", which it did from the start. However, the GUI indicates that I have "1024x768" "800x600" "640x480" "960x720" "864x648". And adding 1280x1024 in xorg.conf doesn't do anything. The added entry does not show up via the GUI after reboot.

So my question is, where does the GUI pull the newly added entries by Envy from? And how on earth can I increase the resolution if manually entering it doesn't help?

---

### Post by Rocket2DMn on 2007-08-02
Manually editing xorg.conf rarely works, the best option is to use the reconifiguration program.
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a process of declaring your hardware, including video driver and resolutions.  Use TAB to move around and SPACEBAR to select/enable.  When you get to the resolutions page, select your monitor's max resolution and everything less.  After you're finished, restart X with CTRL+ALT+BACKSPACE.  This will kill all GUI apps, so be sure you save anything that's open.

---

### Post by ReaderRat on 2007-08-02
To add higher resolutions (and refresh rates) try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you get to the resolutions page, pick those you want - by moving up or down with the arrow keys - and choose or delete the ones you want with the "SPACE" bar.

---

### Post by MockY on 2007-08-04
I have now tried meny different things, and it either crashes xserver or simply doesn't change anything. So after being a gamer for many years and thus a fan of ATi, I now found myself buying a Nvidia product. That is the first time since the Voodoo series was released for the first time by 3dfx.

This time a passively cooled Gforce 8500 was purchased.

---

