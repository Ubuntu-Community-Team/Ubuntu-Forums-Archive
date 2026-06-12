---
title: "[SOLVED] Boot problems"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by lmlypfan on 2007-10-31
Built my first complete system about a month ago. 
Lately, when I hit power, it sounds like its booting, but it doesn't.
Everything has power, just no boot.
I have to hit reset either once or twice, then it boots up.
Ive poked around the interwebs, and some say it might be a RAM issue.

Any thoughts?

---

### Post by taurus on 2007-10-31
When you first turn on your machine, do you see GRUB menu with a few options that you can boot from?  There is one called memtest+ so if you suspect it's your RAM, you should pick that option to test your RAM.

If you don't see the menu, press Esc key to bring it up.  Remember, you have 3 seconds to press it or it will boot Ubuntu.

---

### Post by underdog512 on 2007-10-31
do you hear any beeps indicating that it has performed a POST (Power On Self Test)? Based what you have stated, I do not see how it could be related to RAM.

---

### Post by IIIV on 2007-10-31
Hi. Maybe it's doing a hard disk check during boot... Gutsy is set to do that every 30 boot ups... And each checking takes a couple of minutes.

---

### Post by lmlypfan on 2007-10-31
It never gets to the GRUB menu, and I have never gotten the post boot beep.
I have run a memory test and didn't get any errors.

---

### Post by lmlypfan on 2007-10-31
Its not the hard disk check every 30 boots either.
Thanks for all the suggestions so far.

---

### Post by lmlypfan on 2007-10-31
any other thoughts?

---

### Post by oilchangeguy on 2007-10-31
> **lmlypfan said:**
> Built my first complete system about a month ago. 
Lately, when I hit power, it sounds like its booting, but it doesn't.
Everything has power, just no boot.
I have to hit reset either once or twice, then it boots up.
Ive poked around the interwebs, and some say it might be a RAM issue.

Any thoughts?

this sounds like a power supply problem. you probably used a cabinet with a cheap power supply, or one that is under 400 watts. get yourself a 600 watt. your computer will thank you.

---

### Post by lmlypfan on 2007-10-31
I'm using a Corsair HX620 watt modular power supply. It wasn't cheap IMO

---

### Post by MrWhipplesNipple on 2007-10-31
Hi Imlypfan,
    Sorry to hear that you are having problems.  I must confess, I'm a Linux noob, but I have a ton of hardware exp.  Have you tried re-seating the processor and/or power supply connection to the mobo?

---

### Post by oilchangeguy on 2007-10-31
> **lmlypfan said:**
> I'm using a Corsair HX620 watt modular power supply. It wasn't cheap IMO

doesn't mean it's not bad. do you have another power supply you can try? i had this same problem with a computer about 2 years ago, and it was the psu.

---

### Post by lmlypfan on 2007-10-31
MrWhippleNipple,

I have not tried reseting the processor or power supply connection.  I assume I am to unplug the connections from the power supply to the mother board then connect them back, and also remove and and reinstall my processor?

---

### Post by oilchangeguy on 2007-10-31
> **lmlypfan said:**
> MrWhippleNipple,

I have not tried reseting the processor or power supply connection.  I assume I am to unplug the connections from the power supply to the mother board then connect them back, and also remove and and reinstall my processor?

check the power supply connection. but leave the cpu alone. if there were a problem with it, the computer would be rebooting, on it's own. if you have another desktop, and 15 minutes, you can test my bad power supply theory.

---

### Post by SunnyRabbiera on 2007-10-31
if this is a power issue, it might be best to open your computer up.
BIG WARNING:
If you have a bestec power unit, BACK UP YOUR DATA IF YOU CAN! 
they are really crappy power units.

---

### Post by lmlypfan on 2007-10-31
I'll take a look at the power 2 connections to the motherboard tomorrow.  Thanks for all the suggestions.  If it continues, I'll try another power supply.

Thanks again!

---

### Post by underdog512 on 2007-11-01
> **lmlypfan said:**
> It never gets to the GRUB menu, and I have never gotten the post boot beep.
I have run a memory test and didn't get any errors.

This is definitely not a RAM issue.  I don't belive it is a power supply issue either because most power supplies (even the cheap ones) will at least turn the computer on and get to post before they have a problem.  try checking simple thing.  make sure the power switch isn't sticking and that the it is make good connection to the motherboard.

---

### Post by lmlypfan on 2007-12-15
This was a motherboard issue.  Replaced the board and everything works great.  Thanks for all the help.

---

