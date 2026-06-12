---
title: "Issue installing Ubuntu 11.04 on iMac 27&quot;"
date: 2011-05-15
forum: Apple Hardware Users
---

### Post by fiatlux88 on 2011-05-15
I am unable to get anything graphical to show (screen just turns black) when trying to install Ubuntu 11.04 on my 27" iMac. I can get the CD to boot, but once I select install, after a few moments the screen turns black and stays that way. I can hear the CD making noise while the screen is black.

CTRL-ALT-F1 does nothing. I have also tried many (but not all) vga=XXX install parameters and none of them work. I have a monitor hooked to the mini-display port, and it shows the same thing as the iMac monitor. I used the alternate install CD and I am able to get Ubuntu installed, but when I boot it the same thing happens and I am unable to get to a prompt.

My iMac has a ATI Radeon HD 4850. I am running low on things to try, so does anyone have any ideas what could be wrong?

Thanks.

---

### Post by zacbarton on 2011-05-16
I found that adding "nomodeset xforcevesa" got me booting tho the resolution will be wrong.

---

### Post by JohnAtilano on 2011-05-16
> **zacbarton said:**
> I found that adding "nomodeset xforcevesa" got me booting tho the resolution will be wrong.

nomodeset worked for me.  Boot from live cd.  You'll see a pic at the bottom of your screen showing a keyboard and a man.  Press any key.

You'll see the options to try ubuntu, install ubuntu, etc.

Press F6.  Scroll down to "nomodeset" press enter to put an "X" next to it.  Press "Esc."

Choose "Try Ubuntu.." let it boot up.  Then install from there.

This worked for me on my MBP 5,1.

---

### Post by fiatlux88 on 2011-05-25
I used "nomodeset xforcevesa" as an install option and it worked!

Using just "nomodeset" didn't work for me.

Thanks for you help.

---

