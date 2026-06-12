---
title: "*Sometimes* it works, sometimes it doesn't"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Sam Peters on 2007-09-10
So my ubuntu has been working ok for awhile, albeit I've had to do some serious forum-searching to get it that way. However, I have a lot of 'sometimes' issues. I'll make a cute lil' list:

1.) Sometimes the CD Drive won't read disks. If i sit there and re-insert the CD over and over, try logging out/restarting, and leave the room for awhile and come back, it usually starts working. But is there a way to get it to work *every time*?

2.) Sometimes my WUSB54GSC Linksys network adapter works. I spent a lot of time making sure the ndiswrapper was set up right and all the right drivers were installed, and that the power is going to it and everything, and finally got it working. Then I came back the next day and it doesn't work. I put my old adapter in, which works fine, did whatever for like 5 minutes, then tried the new one again and BAM, works perfectly. ????

3.) Every once in a blue moon both my keyboard and mouse just freeze up and start blinking and I have to manual shut down with the holding down of the power button and what have you.

4.) I get these weird little keyboard input freeze-ups where something like thissssssssssssss happens and it repeats a letter about 20 times then goes on about its business as if nothing had happened. It's really annoying when it happens on the backspace key.

That's all I can think of right now. Anybody got any similar problems? I'm trying to figure out if it's a hardware issue or a software problem with the CD drive, but all this stuff worked when I had Windows.

My keyboard came from an HP, as did the mouse, and I think the cd rom did too but I may have gotten it someplace else. AMD athlon 64 processor, biostar mobo.

---

### Post by cmnorton on 2007-09-10
I would start looking at your log files, /var/log/messages for a start. 

Are the keyboard and mouse USB or PS/2?

In general, it sounds like you need to run some diagnostics to make sure your RAM and hard drive are OK. I do not know what to recommend other than to search this forum and Google for linux diagnostics.

---

### Post by Sam Peters on 2007-09-10
they're PS/2.

I know the hard drive is ok; like i said it worked fine on windows.

---

### Post by Boaslad on 2007-09-10
I had a similar problem with an old computer of mine. I was using windows at the time but the same "inconsistency" problem was there. I was dead set against upgrading the hardware until I had that software problem fixed. I took it to several shops and no one could come up with a solution. Finally, I just kind of gave up, and replaced the motherboard any how. I haven't had a problem with it since. The only thing I can think of is that maybe my hardware had gone bad. It wasn't a cheep solution.. but it did solve my problem.
      P.S.  My old box was an HP too.

---

### Post by cmnorton on 2007-09-11
> **Sam Peters said:**
> they're PS/2.

I know the hard drive is ok; like i said it worked fine on windows.

I've asked this, because I've had some strange things go on with USB. I have had two Red Hat EL 3 systems go belly-up, because memory modules "kept going bad". It turns out an Adaptect SCSI and SATA controllers were the culprit. The memory modules were fine. 

Unless you can get hold of some diagnostics to prove out it's not an interaction with the hard-drive, whether it worked well on Windows or not, then the suggestion of purchasing a mother board might not be a bad one.

---

### Post by asmoore82 on 2007-09-11
> **Sam Peters said:**
> 3.) Every once in a blue moon both my keyboard and mouse just freeze up and start blinking and I have to manual shut down with the holding down of the power button and what have you.

you are describing a kernel panic most likely caused by some misbehaving hardware.

Test the RAM with the LiveCD for sure before proceding.

(if you have 2 sticks of RAM and onboard VGA, test/swap RAM places/test again!)

---

### Post by Sam Peters on 2007-09-14
thanks guys for the replies... i'll look under the hood. the mobo is brand new though, and the old one was an HP (which is why I replaced it). bet it is the ram.

---

