---
title: "Can't boot live cd"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Geek Dog on 2006-09-03
Howdy!

I have been running Debian for some time. I want to try Ubuntu. I downloaded the cd iso and burned it. The box boots from the cd OK, I choose the first option in the menu. Loading starts, but after 'starting x ' it goes to a blinking cursor and sits there. I tried 'safe graphics mode'. It goes a bit further, but goes toa restart and stalls again, with the blinking cursor... Any suggestions?

TIA
Geek Dog

---

### Post by pyros on 2006-09-03
Have you tried testing the cd?

---

### Post by Geek Dog on 2006-09-03
Yes. All is OK

---

### Post by jorn on 2006-09-03
I think the installer canot find correct settings for your screen.
What monitor and graficcard are you using?

---

### Post by Geek Dog on 2006-09-03
Old Stuff. The graphics is onboard, VGA compatible 82810E DC-133, the monitor is an Impression5VX.

---

### Post by jorn on 2006-09-04
Try pressing:
Ctr+Alt+F2

you are prompted for username and password.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confbackup

will save a copy of the file that sets up your display. 

> sudo dpkg-reconfigure xserver-xorg
will make a new setup and maybe you have to know the exact horisontal and vertical sync rate of your monitor, You can try without in the first place.
Sync rates can you find on the net if you don't have the manual.
Type:> startx
to see if it works.

---

