---
title: "Help with HP DV5000"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by ComputerMonk on 2007-01-22
I installed "Drapper Drake" 6.06 successfully on my HP DV5000, but I cannot get Ubuntu to function in widescreen mode. In fact 1024x768 is the only screen resolution that shows up. What do I need to install and what settings do I need to change to use widescreen? I don't know my way around linux yet.

---

### Post by Shatrat on 2007-01-22
I have a DV5000 and I believe it worked at 1280x800 by default for me.
Try the following in a terminal.
gksudo gedit /etc/X11/xorg.conf

scroll down to the Screen section and add 1280x800 to all the mode lines so they look something like this. 
        Modes      "1280x800" "1024x768" "800x600" "640x480"

Then save and exit, and use ctrl alt backspace to restart the X server.
If that doesn't work you may need to install the fglrx display drivers.

---

### Post by Richard Kut on 2007-01-22
Hi ComputerMonk! You might be interested in this:

[http://ubuntuforums.org/showthread.php?t=156243](http://ubuntuforums.org/showthread.php?t=156243)

Enjoy, and good luck!

---

### Post by ComputerMonk on 2007-01-26
:D   I did some research on my problem, and it turns out that there is a flaw with Intel's integrated graphics chipset. (Thinkpad and MacBook users will have the same trouble!) The solution is to establish a connection to the Internet and then run *sudo apt-get install 915resolution*. The latest version on this package works automatically, and no further configuration is necessary. All I did was reboot Ubuntu.

I'm answering my own question here for the benifit of future users.

</computermonk>

---

