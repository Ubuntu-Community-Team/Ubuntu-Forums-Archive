---
title: "Sound problems with notebook"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-05-22
I am having problems with my volume on my Toshiba Satellite A100-SK9. I checked out the DebugginSoundProblems site: ([https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)), but didn't find a solution here. Since it works properly some of the time, I thought that it might be a probelm with the driver. I went to the Realteck site to get the linux driver to try and install it. However I received these errors:



configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 102: alsaconf: not found


Can someone help me to fix them?

---

### Post by angryfirelord on 2007-05-23
Make sure that alsa-base & alsa-utils are installed. You can also try installing alsa-source, but I doubt that would help.

Instead, I'd recommend running **sudo alsaconf** and let alsa build the driver for you.

---

