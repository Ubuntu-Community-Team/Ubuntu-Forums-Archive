---
title: "GUI Startup"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by renegade_ewok on 2007-02-20
Earlier today I ran some updates on automatix.  Shut my computer off and come back later and when it turn it on no gui starts up, just sends you right to the terminal.  I did a reconfiguration and got the GUI running, however there are still a few problems.

Whenever I do a Cntrl + Alt + Del to restart it kicks me back to the terminal and kills the GUI.  Same goes for a hard reboot.

Colors are perfectly fine but when I scroll pages it does the really slow low-refresh rate scroll.

Am I missing something?  Do I have to manually assign the GUI to automatically boot at each reboot?  I also checked my latest version of nVidia drivers and they are up to date.  When I re-configured I used the versa (I think) driver set.  How do I manually assign my own driver set?

---

### Post by renegade_ewok on 2007-02-20
Some further information about this:

Whenever I do a Cntrl,alt,del the errors read like this:

Errors from xkbcomp are not fatal to the x server

After that a bunch of errors which include failure to acces /dev/wacom - the file or directory doesnt exist

xinit: connection to x server lost

Anyone have an idea what this could be?

*edit* This is on 6.10 and I have a 6800GT as my video card.

---

### Post by Blutack on 2007-02-20
I had this once.
The best fix is to run
sudo dpkg-reconfigure xserver-xorg
from the command line.  Just take the defaults and you should be ok.

---

### Post by Patrick K on 2007-02-20
It's possible you need to reinstall the video drivers. Here is a suggestion, edit xorg.conf and replace 'nvidia" with "nv". This with put the system on the defualt generic nvidia driver. Download the newest version of the Envy script ([http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499))  and install it. Go to a console and type envy. Select uninstall nvidia drivers. After it finishes, select install nvidia drivers. It will download the latest driver for you card. 

This is the only thing I can think of that might solve your display problem. Good luck

---

### Post by renegade_ewok on 2007-02-20
> **Blutack said:**
> I had this once.
The best fix is to run
sudo dpkg-reconfigure xserver-xorg
from the command line.  Just take the defaults and you should be ok.
I did that, whenever I re-configure it, it will work no problem the first time.  However the next reboot or the next Cntrl, Alt, Del I do it errors once again.

---

### Post by jasonlfunk on 2007-02-20
The ctrl-alt-del is the shortcut to kill the Xserver. That is supposed to happen.

---

