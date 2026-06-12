---
title: "Cursor and windows going crazy"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-04-19
If this was XP I'd be hunting for a virus! Sometimes my cursor rushes madly round the screen, menus open without being clicked, windows open (I just had about 8 Wastebasket windows open up!), desktop switches to another workspace.

I've been running Dapper since December, and this has only started in the last few days. Here's the last few entries from my system log - seems to be a mouse problem?

Apr 19 12:22:02 dianne-desktop kernel: [17180217.092000] psmouse.c: bad data from KBC - timeout
Apr 19 12:22:02 dianne-desktop kernel: [17180217.112000] psmouse.c: bad data from KBC - bad parity
Apr 19 12:22:02 dianne-desktop kernel: [17180217.116000] psmouse.c: bad data from KBC - bad parity
Apr 19 12:22:02 dianne-desktop kernel: [17180217.124000] psmouse.c: bad data from KBC - timeout
Apr 19 12:22:02 dianne-desktop kernel: [17180217.128000] psmouse.c: bad data from KBC - timeout
Apr 19 12:22:02 dianne-desktop kernel: [17180217.128000] psmouse.c: bad data from KBC - bad parity
Apr 19 12:22:02 dianne-desktop kernel: [17180217.136000] psmouse.c: bad data from KBC - bad parity
Apr 19 12:22:03 dianne-desktop kernel: [17180218.648000] psmouse.c: bad data from KBC - timeout
Apr 19 12:22:06 dianne-desktop kernel: [17180220.980000] psmouse.c: <NULL> at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Apr 19 12:22:35 dianne-desktop gconfd (root-5469): GConf server is not in use, shutting down.
Apr 19 12:22:35 dianne-desktop gconfd (root-5469): Exiting

---

### Post by petersjm on 2007-04-19
I wouldn't have a clue what's going on, but -- and this may sound rather silly -- can you check to make sure your mouse (and keyboard) are plugged in properly? Just a long shot...

---

### Post by LaRoza on 2007-04-19
Are you using a wireless mouse. I don't know about Ubuntu, but that is exactly what happens when you play and Xbox with a wireless controller.

---

### Post by x1a4 on 2007-04-19
Hi,

I've had this issue a few years back and it turned out the problem was the mouse sending random signals.  Once I replaced it everything went back to normal.

---

### Post by freesitebuilder on 2007-04-19
It's not a wireless mouse - but I did plug in a data cable for my phone yesterday. That's the only change I've made, so I'll take that off and see if that cures it. But if it was that, I wuld have thought it would be constant rather than random. Hope I haven't broken Ubuntu already. :)

---

### Post by LaRoza on 2007-04-19
As one of the previous posters said, it sounds like your mouse.

I know Ubuntu 6.06 supported any mouse I put into it including PS/2, USB Dual Scroll, and a USB mouse on an adapter to PS/2.

Random clicking points to the mouse as being the culprit.

Do you have another mouse?

If you don't, it is always a good idea to keep more than one mouse as backup, if you thing about it, the mouse is the easiest thing to break, especially if it has moving parts.

If all else fails, you can use the terminal and key board shortcuts.

---

### Post by freesitebuilder on 2007-06-11
For anyone else with this problem, there is now a bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/119194)

---

