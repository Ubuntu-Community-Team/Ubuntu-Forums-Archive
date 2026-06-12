---
title: "Blank Screen after Dapper Install"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by CarpKing on 2006-06-22
I recently installed Ubuntu 6.06 using the alternate install cd.  The process seemed to go without a hitch, but when it came time to start X, I was presented with a black screen and a message from my monitor of "Not Optimum Mode: Recommended Mode 1280x1024 60hz," and then just a black screen.  I have booted into recovery mode and run dpkg xserver-xorg, but it still has the same problem.  

My leads- I get the same message from my monitor when booting into knoppix; to get it to work I had to type "knoppix screen=1280x1024 vrefresh=60

-when I try to edit xorg.conf, it seems to be a blank file

-at the end of recovery mode, it complains about sd drivers

Any help would be appreciated.

---

### Post by bikeboy on 2006-06-22
Which driver did you select when running dpkg-reconfigure xserver-xorg?
Also, give us the brand & model of your monitor so that we can find the correct vert and horiz sync rates to enter.

---

### Post by CarpKing on 2006-06-23
Monitor is a Samsung SyncMaster 712n LCD.

---

### Post by bikeboy on 2006-06-23
Ok, I would suggest running ```
sudo dpkg-reconfigure xserver-xorg"
```Then select the vesa driver (safe bet), then later when it asks select expert mode. After a quick search I found the specs you will need to enter.
Horizontal: 30-81KHz
Vertical: 56-75KHz

It may help to install the drivers for your video card also, what do you have?

FYI the xorg.conf file can be found in /etc/X11 . So you might need to do this if you go to edit it manually again. 
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
sudo nano xorg.conf
```

---

### Post by CarpKing on 2006-06-23
I selected vesa in xserver-xorg and set the resolution, vrefresh, and hrefresh.  Now when I type "startx" it still brings up the monitor error, but it moves slowly around the  screen and does not go to black.  This now looks exactly like the problem I have when I boot up in knoppix.  However, now when I push ctrl+alt+F1 it puts me into a non-graphical login dialog, which seems like it might be an improvement over before.  In recovery mode, typing "whereis xorg.conf" returns "xorg: usr/lib/xorg" and "cd /etc/x11" returns "bash: cd: /etc/x11: no such file or directory."

My video card is an ATI All-in-Wonder Radeon 9600.

---

### Post by bikeboy on 2006-06-24
That's interesting, I'm absolutely certain there should be an xorg.conf in /etc/X11. Try "locate xorg.conf", it should be the 1st one that comes up.

On second thought, make sure you type "X11" not "x11", it's a capital X.

ATI cards aren't always the easiest to get going in Linux, not sure about the All in Wonders but I have gotten a 9250 going with the official ATI drivers before so it should be possible

---

### Post by CarpKing on 2006-06-24
Hmmm... I don't remember if I capitalized it or not.  I do know that using the "locate" function produced an error.  In the meantime I reinstalled Breezy.  When I get the time again I'll try to upgrade again.  Maybe by then this problem someone will have happened upon a solution.  Thank you for your help in any case.

edit- I also tried editing the conf file for gdm (as mentioned in another thread), but the file wouldn't open and I got an error.  I got the same error when trying to reinstall gdm.  I'll probably investigate that more when I try again.

---

### Post by CarpKing on 2006-06-28
Problem solved!  I reinstalled Dapper from the alternative install cd; after rebooting I had the same problem as last time.  I then rebooted into recovery mode and installed the ATI binary drivers as seen in the wiki: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I then ran dpkg-reconfigure xserver-xorg and selected "fglrx."  After typing startx, gnome started up but popped up some strange errors and lacked some menu items, so I pushed ctrl+alt+backspace and went back into text-only mode (x failed to restart).  I typed apt-get update and apt-get upgrade, and the rebooted into normal mode and everything was normal.  

Still not sure what the gdm problem I was getting before was about, but everything seems to be running smoothly now.  I hope this helps someone; I'm putting the driver howto in my sig.

---

