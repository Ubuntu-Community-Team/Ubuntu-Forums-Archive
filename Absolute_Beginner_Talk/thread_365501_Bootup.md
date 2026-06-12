---
title: "Bootup"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by ~Wayne~ on 2007-02-19
Right so I eventually installed Ubuntu 6.10 after being  a windows user for years.

I installed it and when I click to boot it up for the first time the Ubuntu logo appears and the bar loads fine, then the screen is still obviously turned on but theres just a black background...

What do I do?

Thanks in advance

---

### Post by meng on 2007-02-19
ctrl-alt-f1
log into text console

sudo dpkg-reconfigure xserver-xorg
(enter user password and Enter when prompted)

look for the opportunity to specify resolution/refresh rate.

For example, I wonder if the problem may be that you have an LCD monitor, and it is trying to send a refresh rate higher than 60 Hz.

---

### Post by ~Wayne~ on 2007-02-19
Where do I press that? I tried at different stages yet it does nothing...

What step do I hit the 3 buttons?

---

### Post by Tomosaur on 2007-02-19
Try booting into recovery mode from the main bootup menu, rather than the Ctrl+Alt+f1 combo. Recovery mode will give you a command line, from which you can run dpkg-reconfigure xserver-xorg

---

### Post by n8bounds on 2007-02-19
also, from the initial live cd menu, dont just hit enter or let the time run out, hit F6 and remove the bit about "quiet splash" so you can see whats going on

..that'll help you determine whats hanging..

oh, and check the CD for defects (theres a tool right there on the first menu for that)

---

### Post by ~Wayne~ on 2007-02-21
Ok I tried all this and got nothing, still a lovely black screen!

Could it be my graphics card? I am using an ATI Raedon 9550, problem with the drivers perhaps?

Thanks, Wayne.

---

### Post by n8bounds on 2007-02-21
unsure....try the alternate install cd???

---

