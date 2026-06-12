---
title: "diagnosing random crashes"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2007-11-12
Hi,

I've recently installed Ubuntu (Feisty Fawn) on a friend's laptop, and it's extremely prone to crashing.  I'm wondering how to diagnose what's causing it?  It happens seemingly at random, usually within 20 minutes of switching it on.  Firstly, it starts responding extremely slowly, for about 15 seconds, then everything disappears except the desktop background and the mouse pointer (which is movable), then after about another minute it hangs completely.  I've tried switching to another terminal (ctrl-alt-f1) but it doesn't work.

thanks!

---

### Post by chrismine on 2007-11-12
Have you tried to diagnose the memory with memtest?
Can you check if the laptop is running hot?

---

### Post by Big_Croc7 on 2007-11-12
Memtest didn't flag up anything; I did think about temperature issues, but I don't know how to measure the temperatures - I can't seem to get any program working that will report temps, and they also don't show up anywhere in the bios.  It runs ok under windows though, so if there is a temperature problem it's being caused by software.  Is there any way I can check the temperature accurately?

---

### Post by chrismine on 2007-11-12
Maybe there is an option in the BIOS but you check quickly after the laptop froze otherwise i will have cool down. Some voltage meters do have an temperature meter.

This is as far as I can help - try to cool the laptop with an external fan and see if it keeps up longer before freezing. Maybe it gives you enough time to get lmsensors to work.

I have seen issues with heat and laptops in the forums.

Sorry I could not be of more help.

---

### Post by Hospadar on 2007-11-12
What sort of hardware are you using? sometimes crashes like this are caused by buggy hardware/drivers.  I had a usb wifi reciever a while ago that caused my machine to crash in a similar way.

---

### Post by Big_Croc7 on 2007-11-13
I didn't try looking too hard for temps, as there wasn't anything in the bios I assumed that there weren't any available sensors.  Will try again; thanx for the wifi lead too - will follow that up (I think it has inbuilt wifi of some sort).  It's an Acer laptop of some sort, but I can't remember the other details.

---

