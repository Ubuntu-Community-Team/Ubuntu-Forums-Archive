---
title: "Black screen when installing Gutsy"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Shad0wguy on 2007-10-30
I am sorry if this has been discussed before but I am completely lost.

I am new to Linux.  I downloaded the ISO of Gutsy and burned it to a CD.  I tried to install it on my desktop PC.  When I select to begin the install My screen flickers a few times and then comes up with the No Signal message.  I have tried doing it in VGA, 800x600, and 1024x768.  I am having no luck with this.

FYI, my monitor is my 27" LCD TV.  I was able to run Windows on it fine at any resolution.  When the screen goes black if I hit info on my remote it says that it is running at 85hz which I believe is out of range for that display.

My PC has an AMD Athlon 64 3000+, 1GB RAM, and an ATi Radeon X800XL.

Please, any input would be appreciated.

---

### Post by NT4usB on 2007-10-30
...simple solution is plug it into a monitor to do the install, reconfigure xorg, then switch to the TV.
I'm guessing you already knew that though...
Be careful you don't kill your TV using a too high refresh rate.
You might be able to install from the alternate (server?) install iso/disk. Install a command line system then add the display manager-Xserver after you get it installed.
It will still break the video but at that point you can Ctrl+Alt+F1 to a terminal and manually edit xorg.conf.

---

### Post by Shad0wguy on 2007-10-30
I'll give that a try.  Thanks for the help.

---

