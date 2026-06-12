---
title: "[SOLVED] wireless problem: pty option precludes specifying device name"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by alexmoon on 2007-05-14
I've been trying to connect to my uni network, and despite some really helpful people at the helpdesk and computer club I'm still not having any luck. 

At home I'm using a USB modem, which connects to my home network ok and worked out of the box. I tried it at uni and had no luck, so I've also tried using my pre-linux wireless card, a D-link airplus g dwl-g630. Unfortunately while feisty seems to recognise it now, that doesn't solve my problems.

Both the USB modem and the wireless card will pick up the network (I can tell because I can see other people's playlists on rhythmbox, although not access them), but they won't let me connect. The error I get when I try to connect according to the instructions ([http://www.snap.uwa.edu.au/linux_setup_instructions.html](http://www.snap.uwa.edu.au/linux_setup_instructions.html)) goes like this:

root@alexmoon-laptop:/home/alexmoon# pptp 130.95.11.2 call snap
/usr/sbin/pppd: pty option precludes specifying device name

I figure this has something to do with fiddling done to get the USB wireless modem working, but I don't know where to start looking.

Thanks for any advice that you can offer.

---

### Post by alexmoon on 2007-06-10
*cough cough* ?

---

