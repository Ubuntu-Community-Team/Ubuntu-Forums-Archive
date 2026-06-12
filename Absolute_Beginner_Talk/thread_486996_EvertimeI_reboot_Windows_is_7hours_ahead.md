---
title: "EvertimeI reboot Windows is 7hours ahead"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-28
I running a dual boot w/fiesty and xppro and whenever I switch from Ubuntu and boot up Windows (this is becoming less frequent BTW), the PC's time clock is 7 hours ahead.  I thought that maybe when I set up Ubuntu, I could have screwed up and said that I was in the wrong timezone but i'm certain that I did not make that mistake.  Windows time update gets and error too when I try to sync.  If anyone has an idea about what's going on, please let me know.

VC

---

### Post by justin whitaker on 2007-06-28
What can we say: Ubuntu is very forward thinking. ;)

---

### Post by chandler on 2007-06-28
You said your system clock is set to UTC and I imagine you live in the Mountain Region of the States?  Ubuntu sets the Hardware Clock to UTC.  I think you can double click the Time in Ubuntu and change it.

---

### Post by starcraft.man on 2007-06-28
> **videocheez said:**
> I running a dual boot w/fiesty and xppro and whenever I switch from Ubuntu and boot up Windows (this is becoming less frequent BTW), the PC's time clock is 7 hours ahead.  I thought that maybe when I set up Ubuntu, I could have screwed up and said that I was in the wrong timezone but i'm certain that I did not make that mistake.  Windows time update gets and error too when I try to sync.  If anyone has an idea about what's going on, please let me know.

VC

Boot into Ubuntu, then right click on the time select preferences and uncheck use UTC. This should do it, I think thats it. It's only windows that doesn't behave well with UTC from what I've seen.

---

### Post by videocheez on 2007-06-28
> **chandler said:**
> You said your system clock is set to UTC and I imagine you live in the Mountain Region of the States?  Ubuntu sets the Hardware Clock to UTC.  I think you can double click the Time in Ubuntu and change it.

I'm actually in California and I could be off on the time, perhaps its 8 hours?  What should I change in Ubuntu to fix this?  I never said that my system clock is set to UTC.  I fact, I don't even know how to set my system clock.

---

### Post by reset3x on 2007-06-28
I've noticed that after I install Ubuntu on my PC's the BIOS clock gets set to GMT... Maybe thats the issue?

---

### Post by videocheez on 2007-06-28
> **reset3x said:**
> I've noticed that after I install Ubuntu on my PC's the BIOS clock gets set to GMT... Maybe thats the issue?
that sound reasonable.  Is there a problem with changing the BIOS to another time standard?  Maybe Ubuntu will not be happy.

---

### Post by reset3x on 2007-06-28
> **videocheez said:**
> that sound reasonable.  Is there a problem with changing the BIOS to another time standard?  Maybe Ubuntu will not be happy.

I've fiddled with it and always seemed to lose... When I've set the time in BIOS it gets hosed in Ubuntu.. Then when I would reset the time in Ubuntu it would just change it in the BIOS again... I haven't used Windows in months so I never pursued this...

---

### Post by chandler on 2007-06-28
Ubuntu shouldn't care...  You can try it.  I knew that it was either windows or linux that were funny with the system clock.

---

### Post by theonlyalterego on 2007-06-28
> **starcraft.man said:**
> Boot into Ubuntu, then right click on the time select preferences and uncheck use UTC. This should do it, I think thats it. It's only windows that doesn't behave well with UTC from what I've seen.

I believe this should solve your problem, ubuntu is probably resetting the clock due to your preferences everytime to boot into ubuntu. Change your ubuntu prefs as described [set ubuntu to the correct timezone] above and I'd expect the problem to go away.

---

### Post by videocheez on 2007-06-28
Thanks a lot.  i'll give it a try when I get how tonight.:D

---

### Post by jsimmons on 2007-07-01
> **theonlyalterego said:**
> I believe this should solve your problem, ubuntu is probably resetting the clock due to your preferences everytime to boot into ubuntu. Change your ubuntu prefs as described [set ubuntu to the correct timezone] above and I'd expect the problem to go away.

Mine is already set to NOT use UTC, and it still happens.  This sounds more like a Linux problem rather than a Ubuntu problem, because Kubunut and Fedore Core 6 did it too.

---

### Post by C.S.Cameron on 2007-07-01
I've had the same 7 hour time switch here in Vancouver every time I boot Ubuntu from a flash drive.
I've unchecked UTC, tried setting Ubuntu back 7 hours, fooling around in Bios, no luck yet.
Cork

---

### Post by HeWhoWalks on 2007-11-04
This is what worked for me:

Change the UTC line in /etc/default/rcS to match the following (sudo gedit /etc/default/rcS):

```
UTC=no
```

Note, if the line isn't there, you need to add it.  Hope this helps someone.

---

### Post by videocheez on 2007-11-04
Thanks I'll give it a try.

---

