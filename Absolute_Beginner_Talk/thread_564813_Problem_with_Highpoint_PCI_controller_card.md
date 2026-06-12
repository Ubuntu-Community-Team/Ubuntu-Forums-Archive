---
title: "Problem with Highpoint PCI controller card"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by tomot on 2007-10-01
I'm running Ubuntu on a Generic Computer which has a P4 2.4ghz CPU with 1024 mb memory.
My main HDD is plugged into IDE 1 Primary Master, and that's all good.

I also have 2 peripheral HDD's that plug into an Highpoint PCI controller Card. 
Ubuntu doesn't like this card. When these 2 peripheral HDD's are plugged into this Card,
Ubuntu gets hung up on booting, at IDE 2 and IDE 3
When I unplug the drives (but with the raid card is still plugged in), Ubuntu boots fine.
Both of these HDD's work great under XP.

So I'm thinking Ubuntu may require a Linux driver for this card:

[http://www.highpoint-tech.com/USA/bios_r100.htm#LinuxDrivers](http://www.highpoint-tech.com/USA/bios_r100.htm#LinuxDrivers)

I'm new to this Linux stuff: 

1. Which of these Linux driver should I download ?
2. What do I have to type in Terminal to install a driver?

TIA!

---

### Post by tomot on 2007-10-02
WOW! after 20 hours I still have no reply to this post. With only 4 views?
(2 of which are mine)
Am I posting this to the right forum?
or are all the Linux Gurus on holidays? :)

My first adventure with Ubuntu goes back 2 weeks ago:
[http://ubuntuforums.org/search.php?searchid=28131590](http://ubuntuforums.org/search.php?searchid=28131590)

The final conclusion was to unplug all my HDD's and then let Ubuntu do a normal install.
That worked! and I'm greatfull for that advice

BUT, when I reconnected my DATA HDD's to the High point controller
Ubuntu would not boot.](*,)

It would appear to me that there is a missing link in the Ubuntu install procedure.
Ubuntu should look for Raid controllers, such as it does to detect Video.

I would really appreciate some help with the 2 questions I posed..... Cheers!

---

