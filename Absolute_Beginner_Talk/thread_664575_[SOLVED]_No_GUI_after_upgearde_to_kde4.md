---
title: "[SOLVED] No GUI after upgearde to kde4"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by thisismalhotra on 2008-01-11
Hey Guys,

Might be really stupid but could not figure it out.

I was using kde 4 beta just to see how kde 4 is. Now since today the final version came out. I went ahead a followed instructions on this link: -

[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

After reboot now, I don't have any GUI on the desktop just a command line.

HELP!!:confused:

---

### Post by OffAxis on 2008-01-11
can you start the x server manually?
```
sudo startx

```
The log file for k is kept in 
/var/log/kdm.log

you should look there to see what failed.

---

### Post by arochester on 2008-01-11
First, make sure that you cannot choose a different session which does have a gui. On the page where you sign in you can choose a session type.

If you can't then open Konsole (Terminal Program) and input > sudo dpkg-reconfigure xserver-xorg. This will start a text-based wizard to reconfigure your xserver. Answer any questions you can yourself. If there are questions you can't answer yourself than go with the given default answer. If at first you don't succeed than try again. If all else fails then choose VESA as the graphics mode. 

This should get your gui back up and going. Be aware that this can knock out any video card you have installed and it may need to be reinstalled.

---

### Post by samir85 on 2008-01-11
> **thisismalhotra said:**
> Hey Guys,

Might be really stupid but could not figure it out.

I was using kde 4 beta just to see how kde 4 is. Now since today the final version came out. I went ahead a followed instructions on this link: -

[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

After reboot now, I don't have any GUI on the desktop just a command line.

HELP!!:confused:

I had that problem. Probably you didnt properly remove the old kde packages. In command line type "apt-get install kubuntu-desktop" and after reboot you should have your things back.

---

### Post by Technoviking on 2008-01-11
This may help.
[http://ubuntu-tutorials.com/2008/01/11/how-to-install-kde-40-in-kubuntu-710/](http://ubuntu-tutorials.com/2008/01/11/how-to-install-kde-40-in-kubuntu-710/)

---

### Post by thisismalhotra on 2008-01-11
Thanks All

issues solved, had to re-install kubuntu-desktop

worked like magic...

KDE4 is definitely faster!!

---

