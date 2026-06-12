---
title: "Monitor powers off/on continuously"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-06-26
I have a pretty big problem with my monitor.  I'm not sure if it's related to Ubuntu or not, but I don't know where else to ask.

Anyway, I was reading the news this morning and I noticed that my monitor was about to go into power saving mode since it had been inactive for some time.  I didn't want it to shut off, so I moved the mouse right as the screen started to turn black.

Once this happened, the monitor would come on for about half a second, then turn off.  It would sit off for about half a second, and turn back on.  This cycle just keeps repeating.

I tried restarting X.  I got to the login screen and the problem persisted.  I logged back into gnome, but nothing changed.  I restarted the machine, nothing happened.  I did a raw power off on the tower, restarted, and even at the GRUB menu the problem persisted.

I've tried unplugging the monitor for minutes in a row, unplugging it from the PC tower, plus doing both of these at the same time.  Nothing is working.

Has anyone else had this happen or heard/read about this?  My monitor is a Tyrus Model:T701DB.

Thanks,

---

### Post by freebird54 on 2007-06-26
The only thought that crosses my mind is that the video could be overheating and shutting itself off.  Is it a card with its own fan (is it working?)?  Is it a laptop system it's attached to (battery troubles? or heat)....

Hope you find it, and it's not expensive!

---

### Post by NewJack on 2007-06-26
Got to agree with FreeBird, sounds like a videocard issue.  How old is your vc?

---

### Post by Sparkster185 on 2007-06-26
I just got a new video card less than two months ago.  It has a heatsink/fan.

I really doubt it's related to that, because even when the PC is turned off, but the monitor is turned on, it still goes off/on/off/on/off/etc.

I tried to RTM and searching Google for some way to reset the monitor, but I couldn't find anything.

Could it be possible that Ubuntu sent the power-off signal to the monitor, but I interrupted it at the wrong instant?  Somehow causing the monitor to be stuck in this half-way state?

---

### Post by freebird54 on 2007-06-26
I can't see that happening in a nondestructive manner, unfortunately.... you could have popped a relay - in which case it would need repair....

I don't think you exactly CAUSED it though - coincidences DO happen....

---

### Post by Sparkster185 on 2007-06-26
I think I've noticed (this could be my imagination) that the longer I leave it unplugged, the longer it stays on.  Maybe it overheated?

Either way, I'm thinking I'm going to have to shell out some $ to a repair center, or hope I can get it fixed under warranty.

Thanks for your help.

---

### Post by Ocxic on 2007-06-26
Take your video card out of your machine and place it somewhere safe for 24 hours(non-metallic surface), also powerdown your sysem and remove the battery on the motherbord if possible, this will reset your bios to default, but thats ok, you can setup everything later.. easily, if anything needs to be changed at all. unplug your monitor aswell.

After 24 hours is up reasseble and power on see if that helps... i had the same problem.. it's iether your monitor or your video card, one of the two is messed up.. i find doing this allows all electric charge to dissapate from the components, and insures at next power on, a good clean surge of power to get things flowing again. it may sound like sillyness but has worked on more then one occasion.

---

### Post by Sparkster185 on 2007-06-26
I'm almost 100% sure it's the monitor itself and not the video card since this happens even when the monitor is disconnected from the PC completely.

I'll try leaving my monitor unplugged and disconnected from the PC for 24 hours.  If this ends up working out, I'll update this thread

---

### Post by impert on 2007-10-07
Sparkster, I'm curious to know how you got on. I had the same problem with a brand new monitor (Hanns G HC194D) on both the Ubuntu PC and my Mac mini. I sent it back of course; the vendor said there was nothing the matter with it, and sent me back a monitor, whether the same or another, I don't know. Anyway, it's worked now for six months without a problem on the Ubuntu box, but when I tried it on the Mac some time ago: on . . off . . on . . off . . It's now back on the Ubuntu box, no problems at present, but I think it's a hardware problem, not Ubuntu or the driver.

---

