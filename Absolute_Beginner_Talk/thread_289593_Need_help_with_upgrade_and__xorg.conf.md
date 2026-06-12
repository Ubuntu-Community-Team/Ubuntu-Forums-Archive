---
title: "Need help with upgrade and  xorg.conf"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by sadalmelik57 on 2006-10-31
I upgraded to 6.10 last night and (unfortunately) I accepted all the new files.  The xorg.conf was replaced.  Now I do not get my desktop when I reboot but I get a message that says, "Failed to start the X server" and "using config file etc/x11/xorg.conf".  Another following message indicates that VESA is not correct.

I have an ATI video card that I suspect is my problem. I've had problems with the display in every Linux installation, but somehow I managed to get Ubuntu 6.06 past the display problems (I think using the "safe graphics" install mode).  I get the terminal prompt, but when I type "ls" I do not see the /etc/x11 folder.  I think I need to edit the xorg.conf file to reflect the ATI video card.  

Can anybody give me some direction to get to the xorg.conf file and what I should do when I get there?

---

### Post by rlozano on 2006-10-31
if you boot in recovery mode, you should be able to go to root prompt. you can access this recovery mode during grub start-up and press esc key.

select recovery mode.

at root promp yo can type: nano /etc/X11/xorg.conf

from there you can edit and reflect your video card config.

another thing you can do, if im not mistaken, is to updrage your driver from the prompt.

hope this helps...

---

### Post by sadalmelik57 on 2006-10-31
Thanks, that did help.  I was able to navigate to the xorg.conf file and I changed the driver first from "VESA" to "ati" then to "fglrx".

The change to ati had no effect - I wind up with error messages saying X Server failed to start using xorg.conf.  

Changing to fglrx did change the video signals but not the end result.  I wind up with no graphics during the boot up process and a black screen at the end.  Previously I would see the Ubuntu symbols during the boot up and a progress bar, now I see text showing what successfully loaded or failed to load and eventually the screen goes blank to black to blank to black three times.  Then the computer stops accessing the hard drive and sits quietly.  The only reaction is when I use ALT-CNTL-DEL two times, whereupon it reboots.

Now I'm lost and I don't have any ideas what to do next.

---

### Post by Tamacracker on 2006-11-12
Hey sadalmelik57, I just figured it out bro.

Do this, restart your machine. Choose recovery mode, once you have command prompt you should notice it's rooted. Then type nano. When nano opens, hold CTRL + R, this will open your file directory. GO through the directory until you find etc - x11 - xorg.config.

Modify what you must modify, then hit CTRL + O search for the same exact file you just opened, and click that very same file: xorg.conf.

It'll ask to over-write, choose yes.
Exit and then type exit, it should bring you onto the log on screen :D

---

