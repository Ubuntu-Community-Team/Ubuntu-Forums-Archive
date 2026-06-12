---
title: "Apps close randomly and ubuntu logs out randomly"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Toam on 2007-07-09
I just installed Ubuntu 7.04 and installed the updates...

I was using Gaim and Opera, and gaim closed randomly. While googling a possible solution, ubuntu logged out, leaving me at the log in screen. I logged in again and opened opera trying to find a solution and opera closed while I was using it. I checked the system log and that closed while I was reading it.

I've got Ubuntu installed on a 35 gig partition with a 5 gig swap partition on an 80 gig drive where the other 40 gig partition contains windows XP. I'm running an AMD Sempron 3000+, with 1gig of ram. Is it likely to be a problem with the ram?

I planned on reinstalling Ubuntu to see what happens but when I loaded the live CD decided to see if apps would close while I was using them. I was using Gaim and Firefox, and it logged out.

Any ideas?

---

### Post by stoodleysnow on 2007-07-09
Perhaps you've been hacked...?
It could be the hardware, but judging by the nature and timing of events, I'd say it's more likely to be a hacker, or perhaps (though very unlikely) a virus?:confused:

---

### Post by Steveway on 2007-07-09
In Linux if a process uses a lot of CPU and RAM, like if it is in loop or hangs then the system kills the process on its own.
Were there big Usage-spykes while those apps closed itself?

---

### Post by Cyvros on 2007-07-09
> **stoodleysnow said:**
> Perhaps you've been hacked...?
It could be the hardware, but judging by the nature and timing of events, I'd say it's more likely to be a hacker, or perhaps (though very unlikely) a virus?:confused:
I didn't think that'd be it - he just installed it and I haven't heard anything about any bugs and/or viruses being found/included in the updates.

Could've been a temporary session problem - reinstallation **should** help.

---

### Post by Toam on 2007-07-09
> **Cyvros said:**
> Could've been a temporary session problem - reinstallation **should** help.

I'm not sure that it will since I ran the live cd and it did the same thing.

---

### Post by Cyvros on 2007-07-09
> **Toam said:**
> I'm not sure that it will since I ran the live cd and it did the same thing.
Just so I can repeat like a parrot: Hardware. :D

---

### Post by Feba on 2007-07-09
driver problem, possibly? Maybe a mainboard problem, if Ubuntu can't use your RAM, it might cause itself to crash.


Have you tried looking in the device manager and seeing what it says? This is very weird, it might be worth trying another distro, if even just a live CD, to see what it does.

---

### Post by lassegs on 2007-07-09
Why dont you open a terminal type in 

gaim

and post the output from the terminal just before i quits here.

---

### Post by Toam on 2007-07-09
I swapped my RAM with my housemate and played around on the live cd for half an hour or so and then reinstalled from that with no problems at all.

I've suspected something about this RAM for ages as windows was resetting about once every 8 or so days, but it was infrequent enough not to bother me...

---

### Post by southernman on 2007-07-09
> **Toam said:**
> I swapped my RAM with my housemate and played around on the live cd for half an hour or so and then reinstalled from that with no problems at all.

I've suspected something about this RAM for ages as windows was resetting about once every 8 or so days, but it was infrequent enough not to bother me...
You can edit your post to say solved now that the ton of bricks have landed on you. Time to buy ram! errrr I mean have your ram rma'ed. Most ram is warrantied for a lifetime.

---

