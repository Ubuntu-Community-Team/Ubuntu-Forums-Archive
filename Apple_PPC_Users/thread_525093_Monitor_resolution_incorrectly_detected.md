---
title: "Monitor resolution incorrectly detected?"
date: 2007-08-13
forum: Apple PPC Users
---

### Post by thevictor390 on 2007-08-13
I just managed to install Ubuntu 7.04 (fiesty?) on a 500 MHz iBook G3.  It boots and runs fine, but the screen resolution has options only for 640 x 480 or 800 x 600 (the latter is the default).  This causes some strange video problems on the 1024 x 768 monitor, mostly that the GUI does not fill the screen, but is pushed to the top-left.  Is there a way to "force" 1024 x 768 (which was automatically detected in 6.10)?

FYI, I'm pretty much a complete newbie at all things linux, but I'm not afraid of the terminal (although I don't like it...)  Thanks in advance!  Hopefully I'll be posting from that computer soon, but it has been doing a software update for a while now...

EDIT: okay, I looked around and found some tutorials for modifying xorg, and it seemed to work.  Sorry for wasting your time, but if anyone has a similar problem, try this topic: [http://ubuntuforums.org/showthread.php?t=89167&highlight=screen+resolution+incorrectly+detected](http://ubuntuforums.org/showthread.php?t=89167&highlight=screen+resolution+incorrectly+detected)

---

### Post by oaklad on 2007-08-14
You will need to reconfigure configure xserver-xorg

See the threat at:

[http://ubuntuforums.org/showthread.php?t=498598](http://ubuntuforums.org/showthread.php?t=498598)

I too had the same problem and I was able to reconfigure xserver-xorg on my iBook G3 dual.

---

