---
title: "[SOLVED] Wacky problem"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-11-11
This is such an odd problem that I'm asking here to help keep my sanity.

I have a brand new power supply CoolMax CR-450 (450 watts, a honey of a power supply)

(([http://www.coolmaxusa.com/productDetailsPower.asp?item=CR-450&](http://www.coolmaxusa.com/productDetailsPower.asp?item=CR-450&)
details=features&subcategory=140mm&category=single)

It has less than 8 hours of use. I have additionally a brand new cpu and mobo.

Intel Celeron D (Model 347) and a FoxConn 661GX7MJ-H motherboard.

Things installed fine. I had the two side panels off the case, from installing devices, etc. Everything worked as expected. I installed Gutsy and ran through hours of updates, and installing all the  "bells & whistles". Finally I buttoned the case up. Next I pushed the power button and the box did not boot. But the fans came on (power supply and cpu). I did a cold un-boot. Unplugged the power cord, pressed the reset button and saw a brief flash of LED, plugged it back in and powered up. Everything worked as expected. Concerned, I powered down and Gutsy shut down normally. Powering up again, no power, and again all the way through BIOS POST, started to load Gutsy, put the splash screen up and started filling the "status bar". Hung, cold un-booted. Waited 30 seconds, powered up, optical drive LEDS blinked and then everything went dead, except the fans. Powered down and up and up and down and then put the box on it's side and everything went back to working OK. Then not.

At first, I thought it was a bad power supply, but it seems OK. Then I thought the PSU connectors were flaky, but they aren't. Next I thought the BIOS was bad, but I'm online now (with the box horizonal; the computer is unhappy when it is vertical). It is a brand new CMOS battery. I tried googleing "power supply, vertical, horizontal, troubleshoot" and I'm going NUTS. If somebody reading this has had ANYTHING similar, please let me know. This is a type of intermittent problem of the very worst sort.

---

### Post by Squizz on 2007-11-11
It might sound like a rookie mistake, but are you sure you've put the washers on properly?  The fact it works when it's on its side could suggest that something is shorting because it's touching the case.

---

### Post by Mark_in_Hollywood on 2007-11-12
By washers I think you mean printed circuit board standoffs and yes they are all where they belong. I had to move them because the case is both ATX and m-ATX size holes. Yet, your post makes some sense. Even so, it's not going to be the standoffs. As for washers, the powersupply was carefully screwed into the case. I grounded myself during all component installations. It's just nuts! The powersupply could be intermittent, but then the fans shouldn't run. It's just nuts. I'm losing sleep over this. Maybe more tomorrow!

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
try to rule out one peasce of hardware at a time

umm gessing  so from far left field memory?
 did you run memtest on it yet
dose the hdr always spin up
ummmm..... ya

---

### Post by robinl on 2007-11-12
It would be good if you start off with the bare essentials first. Take off all your harddrives, optical drives and peripherals, and your graphics card if your motherboard has a built in one. If it works, then add the components one by one until it stops working. Then, try again from the start, this time connect the components in a different order to the first time. If both times the same components cause the computer to fail then it's that component that's causing troubles, but if it changes it's likely that the PSU isn't giving out as much power as the computer needs.

---

### Post by LowSky on 2007-11-12
its not like your runnign a SLi setup or anything crazy, a 450watt power supply is plenty. I bet you have a poorly grounded motherboard... makes sure the motherboard's circuits are not touching any bare metal

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-12
> **robinl said:**
> It would be good if you start off with the bare essentials first. Take off all your harddrives, optical drives and peripherals, and your graphics card if your motherboard has a built in one. If it works, then add the components one by one until it stops working. Then, try again from the start, this time connect the components in a different order to the first time. If both times the same components cause the computer to fail then it's that component that's causing troubles, but if it changes it's likely that the PSU isn't giving out as much power as the computer needs.

ya that sounds good but what a pain lol 
ps good luck

---

### Post by Mark_in_Hollywood on 2007-11-12
OK OK OK 

I did all as was suggested, and when I replaced the video card it went back to working, so I thought the 8x agp had broken.

Never-the-less, I cleaned the gold fingers on the card and then it dawned on me: a brand new motherboard, even though in a high quality static proof bag had developed some oxidation on the contacts. After installing the old card, removing it and re-installing the new card things are working!!!!

---

