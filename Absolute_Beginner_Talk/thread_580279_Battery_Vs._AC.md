---
title: "Battery Vs. AC"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Phaedras on 2007-10-18
Hey guys,

I just installed the Gutsy distribution and im extremely pleased with it. Everything is working splendidly besides 1 thing....

Ubuntu keeps shifting between being on battery power and AC power.. Every 2-7 mins it shifts, which means the dim of the screen changes - which is rather annoying :)

Anyone have an idea why it does that? :confused:

---

### Post by Dr Small on 2007-10-18
Did you previously have windows installed ? Did it do this on Windows ?
This sounds like a power problem, though.

Dr Small

---

### Post by Phaedras on 2007-10-18
> **Dr Small said:**
> Did you previously have windows installed ? Did it do this on Windows ?
This sounds like a power problem, though.

Dr Small

Yea, i have previously had Vista installed.. It never seemed to do anything like this. I tried the old 7.04 distribution with Wubi and it didnt do anything like this either..

---

### Post by Sef on 2007-10-18
Make sure your power cord is fully plugged in.  Possibly it is a bit loose and can't pull enough electricity; hence the problem.

---

### Post by Dr Small on 2007-10-18
It could also be some loose connection on the inside of the box, causing it to switch to DC power.

Dr Small

---

### Post by genbuntu on 2007-10-18
ya I would also make sure if it ever occurred in windows or previous version of ubuntu. Also check if it is sue to a loose connector or plug.

Edit 1: try checking the power profile to see if you can do anything there

---

### Post by Phaedras on 2007-10-18
It does it when the ac is completely disconnected aswell..

I've attached a prntscrn of the my powerhistory the last 40 mins..

---

### Post by Dr Small on 2007-10-18
How on earth can it do that when it has no AC power ?

---

### Post by Phaedras on 2007-10-18
> **Dr Small said:**
> How on earth can it do that when it has no AC power ?

You tell me, i have absolutely no clue :)

Sorta why i asked in here.. hehe

---

### Post by Phaedras on 2007-10-18
Here is another printscreen..

As you can clearly see on the icon the AC is not plugged in although the popup is saying something else..

Its weird..

---

### Post by Dr Small on 2007-10-18
You have one awesome system. :D The system says it runs on AC power when it is not!
I wonder how long that would last.... :)

Dr Small

---

### Post by genbuntu on 2007-10-18
I can only suggest some hit and trials you may try:

1) try removing your battery and put it on ac power and see what happens..

2) try fully recharging your battery and remove ac power and check again

---

### Post by Phaedras on 2007-10-18
> **Dr Small said:**
> You have one awesome system. :D The system says it runs on AC power when it is not!
I wonder how long that would last.... :)

Dr Small

haha, well according to the power history graph i've been on 0 watt for the last 25 mins :D

So i gotta a super economic and environmentally perfect pc i guess :)

But i'd rather have it working...

---

### Post by Phaedras on 2007-10-19
> **genbuntu said:**
> I can only suggest some hit and trials you may try:

1) try removing your battery and put it on ac power and see what happens..

2) try fully recharging your battery and remove ac power and check again


I tried both now, i even did a reinstall of ubuntu..

At the moment im on my laptop and i have the battery removed, but it still changes to "battery power" quite often..

Anyone have the same problem or an idea of how to fix it?

---

### Post by LowSky on 2007-10-19
this isn't happening in windows? seems like a power managemet issue, what kind of laptop is it can you list the specs?

---

### Post by Mr.Beast on 2007-10-19
Sounds like a bug in the power management "features" perhaps.
I have seen quite a lot of power management quirks, but I've not used gutsy yet.
I would setup a new power management profile, or disable all possible power management toolsets.  Also think about the motherboard power management features, ACPI etc.  
It sounds like it's a problem, or an irritation that is easily trackable, so I would change one thing at a time and see if you find the trigger.  (very nice graph BTW, made me chortle)

---

### Post by Phaedras on 2007-10-19
> **LowSky said:**
> this isn't happening in windows? seems like a power managemet issue, what kind of laptop is it can you list the specs?

Nope, i've never had the same problem running in Windows Vista..

The specs are:

Nvidia GeForce 8600M GT 512MB
Intel Core 2 Duo T7500 2.20 FSB800Mhz
100 GB HDD SATA 7200RPM
2 GB DDR2 RAM 677 MHz (2x1024)

---

### Post by Phaedras on 2007-10-19
> **Mr.Beast said:**
> Sounds like a bug in the power management "features" perhaps.
I have seen quite a lot of power management quirks, but I've not used gutsy yet.
I would setup a new power management profile, or disable all possible power management toolsets.  Also think about the motherboard power management features, ACPI etc.  
It sounds like it's a problem, or an irritation that is easily trackable, so I would change one thing at a time and see if you find the trigger.  (very nice graph BTW, made me chortle)

If only i knew how.. Im completely new to Ubuntu, so im rather lost in changing advanced things etc..

And thanks, i thought the graph was nice aswell.. hehe

---

