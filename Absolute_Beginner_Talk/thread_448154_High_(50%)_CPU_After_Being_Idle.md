---
title: "High (50%) CPU After Being Idle"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-05-18
I've been having problems with my CPUI usage after I leave my machine idle for a short amount of time (20 minutes).  When I come back to it, the CPU usage is at 50%.

I have an nVidia graphics card and I installed the drivers via Envy.  This problem didn't used to happen until recently.  I got a new graphics card (my old one died), and ever since then this started.

I'm not quite sure what information will be helpful, so just let me know and I will post what you need me to.

Thanks in advance.

---

### Post by Sparkster185 on 2007-05-18
I forgot to mention this....  If I restart the X-Server (ctrl+alt+backspace), then log in again, it's back to normal.  Also, as long as I'm using the PC, everything is fine.  It's just when I leave it idle this happens.

---

### Post by jackmc on 2007-05-18
could it be a search program (eg beagle) indexing? Try opening system => administration => system monitor, then sort by CPU). I guess when you start using it, it stops using the CPU though.

Conky shows Beagle using a LOT of my CPU when idle, as it indexes files for future searches

---

### Post by Sparkster185 on 2007-05-18
I'm not quite sure.  I will open the System Monitor now and leave the PC idle for a little while.  By the way, I am running Kubuntu.

Thanks for the suggestion.  I will post back here in a little while.

---

### Post by Sparkster185 on 2007-05-19
I just left it untouched for about three hours, came back and it's fine.  Perhaps it has something to do with when the monitor goes into power saving mode.

---

### Post by Sparkster185 on 2007-05-19
When I woke up this morning, the CPU was again hovering around 50%.  Looking at the System Monitor, it tell me that Xorg is taking up 98-99% of my user CPU and 50-52% of the total CPU.

I tried to ctrl+alt+backspace to restart X, and that didn't even respond.  The only thing I could do was to restart the PC via the power button.

This didn't start happening until I got my new graphics card.  Could it be possible the nVidia driver is doing something to X that causes it to devour CPU time and not release it?  I think I've noticed a pattern where the longer I leave it idle, the worse it gets.

Now I'm thinking it might be superkaramba related.  After snooping around for info about Xorg taking high CPU usage, I found someone else with my problem and believes it might be superkaramba.  I will try leaving superkaramba off and seeing if xorg eats my CPU.

---

### Post by rsambuca on 2007-05-19
Obviously sounds related to your new graphics card.  What driver do you have installed, and what is the new card??

---

### Post by Sparkster185 on 2007-05-19
I have a nVidia GeForce FX 5200 (I believe) and I installed the nVidia drivers via Envy.

I am now pretty certain this is a problem with SuperKaramba and the nVidia drivers.  I have turned SuperKaramba off, and Xorg doesn't even appear on the list of processes using my CPU time.

Whether it's a particular widget, or Karamba itself, I'm not sure of.  When I go to bed tonight, I will leave Karamba off, and if my PC isn't at 50% when I wake up, I know it's not the drivers.

---

### Post by Sparkster185 on 2007-05-20
I am almost certain the problem lies in SuperKaramba.  My PC is running beautifully, and it's been sitting idle for well over 12 hours.

---

### Post by rsambuca on 2007-05-20
You should file a bug with the superkaramba developers.

---

