---
title: "Wireless Mouse not working..."
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by DoodlesQ on 2006-04-18
Hi everyone. I just installed Ubuntu on my Dell laptop. I've used Windows almost daily for many, many years but I guess it was time for a change.

So far so good. Got everything running no problem - searching these forums has been a great help. The one roadblock left is that I can't get my Microsoft Optical Wireless mouse working under Ubuntu. I still have winxp in dual boot, and it works fine there, so the hardware end is okay).

After some poking around in I found the device manager - and it actually lists Microsoft Wireless Optical Mouse. However, the cursor is not moving or clicking at all. When the mouse is plugged in, I noticed the "microsoft wireless optical mouse" listing on the left pane of the device manager dissappears and reappears a lot. If I unplug the mouse it seems to just stay there. I have no idea what that means. 

I can still use the laptop touchpad to move the cursor, but I'd hate to do so. Once I get this mouse thing up and running, I think I'll primarily be in Ubuntu for the forseeable future.

Oh, I didn't have the mouse plugged in when I installed. I thought it may cause a problem.

Anyone have any advice? I'm an absolute n00bz0rz here, so if anyone has any ideas on how to fix this, pretend you are explaining them to a child. Or a dinosaur with the intelligence of an average child.

---

### Post by indytim on 2006-04-18
I don't know if this will help or not.  I recently built a new PC for my wife.  When I was configuring (and loading Ubuntu) I used a PS2 mouse.  After I had completed the installation, I then shut down the PC.  I inserted the optical into the USB port and re-started.  Ubuntu picked up the optical mouse and keyboard (both MS) right off and went happy.  

If you haven't tried it yet, shutdown, restart with the optical and sensor plugged in and see what happens.

IndyTim

---

### Post by DoodlesQ on 2006-04-18
Oh - I should have mentioned this - it's the wireless mouse' receiver is USB and it's through a USB hub. Other stuff going through the hub seems to be working okay, so I don't think that's the problem. Again, the setup works fine in Win XP so I think all the connections/hardware are fine.

Alas, I've tried rebooting with the mouse plugged in (even with it plugged in directly, bypassing the HUB). Same issue.

---

### Post by DoodlesQ on 2006-04-18
It looks like, by all accounts, this should "just work". So what am I doing wrong? Should I try reinstalling Ubuntu? I'm afraid this mouse not working would basically kill any chance of me using it.

---

### Post by Kimm on 2006-04-18
Do you have Breezy or Dapper?

If your running Breezy perhaps you should try Dapper. My Wireless Keyboard and Mouse worked out of the box, even though I installed with a PS2 Mouse and Keyboard.

Its seems only logical that Dapper should have something Breezy doesnt, who knows... maby that includes better support for Wireless Mice...

---

### Post by DoodlesQ on 2006-04-18
I was using Breezy, maybe I'll give Dapper a try. Since I'm a n00b anyway, it didn't seem like I really needed to give the beta a try. Perhaps I will though, if you think that will fix it.

---

### Post by DoodlesQ on 2006-04-18
Update: i tried dapper. same exact problem to a T.

This is Microsoft optical mouse 2.0. In device manager 'microsoft optical wireless desktop 2.0' (which this part of) keep going in and out.

---

### Post by Danny Boy on 2006-04-18
I never had a problem with my MS wireless keyboard mouse combo with Breezy. 

Is it possible that Ubuntu's power managment shut off the USB port to conserve power being it's a laptop?

---

### Post by DoodlesQ on 2006-04-18
I'd say it's certainly possible, though I tried it with just the mouse and still no luck.  It's plugged in - How could I check for something like that?

---

### Post by Danny Boy on 2006-04-19
[QUOTE=DoodlesQ]I'd say it's certainly possible, though I tried it with just the mouse and still no luck.  It's plugged in - How could I check for something like that?[/QUOTE]

That the experts will have to answer. I'm still a newbie myself just throwing out an idea. :cool:

---

### Post by DoodlesQ on 2006-04-19
Well here's what I can gather, in case anyone else ever goes looking -

The Microsoft Wireless Desktop works only in PS/2 mode. At the very least, I can't get it working in either Breezy or Dapper. I don't think I've found anyone that got it working with USB, the common thread seems to be PS/2.

---

### Post by Danny Boy on 2006-04-20
that's possible mine was connected to both USB & PS/2. I do know that my new wireless mouse is USB only and works fine with Ubuntu. It's an HP

Keyboards are funny, it's hit or miss getting them to work if they aren't PS/2 connected.

---

### Post by sunshine02 on 2006-04-22
My wireless mouse was working fine until around a week ago, then it quit. It is part of a Microsoft wireless keyboard and mouse combo. I dual boot with Windows XP and they work in XP but the mouse no longer works in Ubuntu, though the keyboard works fine. The mouse just quit; it doesn't click or move. I plugged in a Microsoft USB mouse and that works fine. Anyone have any ideas what may have happened or what I can do to get it back?

---

### Post by Danny Boy on 2006-04-22
[QUOTE=sunshine02]My wireless mouse was working fine until around a week ago, then it quit. It is part of a Microsoft wireless keyboard and mouse combo. I dual boot with Windows XP and they work in XP but the mouse no longer works in Ubuntu, though the keyboard works fine. The mouse just quit; it doesn't click or move. I plugged in a Microsoft USB mouse and that works fine. Anyone have any ideas what may have happened or what I can do to get it back?[/QUOTE]

Is it hooked up to both PS/2 & USB? There seem to be a problem if it's only wired to a USB port.

---

### Post by sunshine02 on 2006-04-22
It has worked for months connected only to the USB port, then quit. I did as you suggested and it's working now...   Thank you very much!

---

### Post by Enrico2 on 2006-11-05
ahhh!!
unresolved thread??
i have the exact same problem! (exactly up to the "will not use ubuntu without the mouse) same mouse and everything.
except here the mouse does work when you restart, for about 5 minutes, then it freezes.
the little led light on the usb keeps working, but if i disconnect it and re-connect, then the led doesn't work anymore.
any help would be appriciated.

p.s.
i'm also a ultra-mega-n00bi-skubi-d00 with linux :).
(but a pro on windows.)

---

