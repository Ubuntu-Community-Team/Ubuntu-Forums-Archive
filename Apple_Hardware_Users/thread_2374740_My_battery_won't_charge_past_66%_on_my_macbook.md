---
title: "My battery won't charge past 66% on my macbook"
date: 2017-10-18
forum: Apple Hardware Users
---

### Post by mike-francis26 on 2017-10-18
I've just swapped over to Ubuntu 17.04 from Mac OS and my battery now won't charge past 66%. It was charging fully yesterday, so I'm guessing it's a compatibility issue?!
Can anyone shed some light on this for me?
Thanks

---

### Post by ubname on 2017-10-18
It may be that the battery is old, and wont charge past 66%, click on the battery icon to see some stats on the wear level

---

### Post by howefield on 2017-10-18
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by mike-francis26 on 2017-10-19
The battery is definitely old, but I'm almost positive is not because as soon as I ran Ubuntu it started happening, also my laptop is having trouble recognising that the charger is plugged in. Seem a bit odd. Could there be any other reasons for this apart from the old crappy battery?!

---

### Post by Bucky Ball on 2017-10-19
> **mike-francis26 said:**
> The battery is definitely old, but I'm almost positive is not because as soon as I ran Ubuntu it started happening, also my laptop is having trouble recognising that the charger is plugged in. Seem a bit odd. Could there be any other reasons for this apart from the old crappy battery?!

The symptoms you describe fit dying battery. That it started happening when you swapped OSs could simply be coincidence. Were you working off the battery during install, etc.? If so, that is a *_very_* bad idea, but besides that, an OS install would draw plenty from the battery and could have been the final straw.

If it's not charging beyond 66%, doubt it's got anything to do with the OS. Use the charge in the battery up, flatten it, and see what it charges to next time, if it charges at all and if it doesn't die a natural death before it runs out of charge.

(Just a note: laptop batteries should be run to flat once in awhile then fully recharged. Only ever charging from half full will shorten the life of the battery. This will no doubt change, and may have already on some newer laptop batteries, in the near future.)

---

### Post by mike-francis26 on 2017-10-21
Thanks for the advice, Let it flatten and re-charged, but still the same (if not less). The thing that makes me think it's not the state of the battery is the fact that when I plug the charger in it takes around a minute for the computer to recognise that it's plugged in. I have been thinking of getting a new battery for a while now, so maybe I'll try that and see if it make s a difference. 

thanks

---

### Post by gabriele-tassoni-gmail on 2017-10-31
hi,
I'm experiencing the same issue, and I have the idea that there's some error on interpreting data coming from battery, or OS X deliberately hiding facts about the battery, I try to explain better my experience:

- Two weeks ago I bought a new battery, still using Mac OS X. Charged the battery 3 times following the advices in the battery's manual. The battery correctly reports 100% when fully charged, since then I recharged the battery only when It was reaching 10% or less, as per manufacturer's advices.
- In the meantime I bought a new hard disk, in which I installed Ubuntu 17.10 all alone as soon as it got released. From the beginnning I noted that the battery was "fully recharging" at a percentage reported of 70%. Wow! I thought, could it be the battery failed in just two weeks?
- Then having kept the old hard disk with OS X intact, I put it inside the macbook and guess what? It reports the correct full charge at 100% (here is the procedure I followed to be sure about this: fully charged the battery in ubuntu, it stucked at 70%, removed the power cable, switched off Ubuntu, replaced the disk with OS X, booted OSX, and it reported 99%, maybe I lost 1% in shutdown, bootup operations).
- As a matter of fact, even the leds indicator built in the macbook, which reports visually using 7 leds the battery level, shows all 7 leds are on when OSX reports 100% (and ubuntu 70%), when OSX reports 70% there are only 6 leds on.

This tells to me that there's at least a misinterpretation of the data read by ubuntu on batteries. Or that OSX is bragging about.

Still need to try to let the computer die on battery and fully recharge using ubuntu, I will try to do it to reset battery, eventhough I won't like to let the OS be switched off the hard way...

Ah, I'm on a MacBook5,1.

Still I have no answer to this issue, but I hope to find someone here that can help me looking for a workaround.

Thanks

---

### Post by ulysses77 on 2017-10-31
This is likely a battery issue. Mac OS X's software probably won't tell you that your battery is bad, but rather it will tell you how full it is relative to the battery's current (reduced) capacity. The Ubuntu installation is likely looking at the original battery's capacity and so when it's charged to the degraded battery's maximum capacity, it'll only register as so much. Battery's are easy to replace though.

---

