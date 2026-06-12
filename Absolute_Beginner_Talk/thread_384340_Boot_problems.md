---
title: "Boot problems"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by omockler on 2007-03-14
Hey Guys I'm having a little bit of trouble.

I just moved to ubuntu 6.10 from windows about 2 months ago and love it, but I managed to break something last night.

I have a 2.8 ghz celeron with 1gb ram, and the install was working fine untill last night when I moved the hardware to a new case and added an DVD-burner.

After moving the hardware I had a few problems that I managed to work out but then the real trouble started.  Once I logged on I couldn't get any sound, It gave me an error like this "gstreamer plugin/ device not found."

After looking through the forums it seemed like all I needed to do was re-add my user to the audio group. I did this but it only made things worse.  Now gnome hangs on startup.

The computer will boot all of the way to the gnome login page and I can enter my username and password but when gnome starts all I see is the orange background and sometimes a blank white window shows up in the top left hand corner.

I can still get on the machine through ssh and login using both the root and default user but the only way I can get onto gnome is by removing all of the groups from the default user.

I also tried to use the live CD and the same thing happened. Thanks for the help!

---

### Post by jimbren on 2007-03-14
it sounds to me like some piece of hardware wasn't properly seated when you moved to your new case, or there's some other hardware issue going on.  

I would make sure that everything is firmly seated, particularly the sound card (assuming it is not onboard, of course), and try it again.

Failing that, disconnect the DVD drive and try.


jimbo

---

### Post by Kobalt on 2007-03-14
> **omockler said:**
> 
I also tried to use the live CD and the same thing happened. 
If the Live CD hangs then it's a hardware problem... 
The DVD drive is unlikely to cause such a problem though. Did you connect a cable from that drive to your soundcard ? If so, you could try to unplug that.

---

### Post by omockler on 2007-03-14
The sound card is on board and the only thing connected to the DVD drive is IDE and power.  I'll try it without the DVD drive when I get home from work.  Thanks for all of the advice so far, lets hope it works.

---

### Post by omockler on 2007-03-15
The on bourd sound card went bad, I all works fine with a new one.

---

### Post by Kobalt on 2007-03-15
Good news ;)

---

