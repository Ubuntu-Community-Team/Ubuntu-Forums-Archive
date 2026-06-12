---
title: "Trouble setting system time in dual boot system"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by john262 on 2006-12-14
I have a dual boot system that boots into Ubuntu 6.06 and Puppy Linux 2.11. It doesn't have Windows installed.

The problem is that I cannot get the system time to sync between Ubuntu and Puppy. When I get the correct time to display in Ubuntu, then boot into Puppy, the time is eight hours into the future. Then if I go ahead and adjust the time back to it's correct setting in Puppy, the time is off by eight hours again when I boot into Ubuntu.

I know that this is just a minor inconvenience because it takes only a few seconds to set the correct time, but i am trying to learn GNU and Linux and I am just curious how to fix this. In Ubuntu I have it set to automatically sync with Internet servers. I tried setting my local time zone off by eight hours in Puppy to get it to sync with Ubuntu but that didn't work.

I don't know if I should be asking this in this forum or the Puppy forum or both but I thought I'd try here first.

I tried to search for an answer to this and found one article talking about the TZ variable and also using the "clock -s" command but I tried that command in the terminal and it said that that command doesn't exist.

---

### Post by adaptr on 2006-12-14
Your timezone is probably set wrong on one of the systems, or one of the systems updates the hardware clock with the timezone-adjusted time (this should not normally happen)
Double-check the timezone synchronisation settings on each system - it doesn't matter what the actual timezones are, since the system time should always be stored in UTC.

---

### Post by john262 on 2006-12-14
Thanks. I am trying to do that but it doesn't seem to work. I also tried changing my system's time in the bios. It had been set to GMT which is eight hours ahead of my local time. So I changed my bios time to my local time, but that didn't seem to fix the problem.

I am still getting that eight hour time difference. Puppy is still eight hours ahead of Ubuntu.

---

### Post by rsambuca on 2006-12-14
I had this same time shifting when I was first dual booting ubuntu and XP.  I would correct one, and then the other one was off.  After getting tired of this, I just left it alone, and after a couple of boots it just corrected itself somehow.

---

### Post by confused57 on 2006-12-14
See reply#5, may help:

[http://www.ubuntuforums.org/showthread.php?t=123004](http://www.ubuntuforums.org/showthread.php?t=123004)

---

### Post by mcduck on 2006-12-14
..you can also change between UTC or normal time if you right-click the clock applet in Gnome and select 'Preferences'.

---

### Post by john262 on 2006-12-14
Thank you very much. I went to /etc/default/rcS and changed the line UTC=yes to UTC=no as suggested in the link you provided. That did the trick.

---

