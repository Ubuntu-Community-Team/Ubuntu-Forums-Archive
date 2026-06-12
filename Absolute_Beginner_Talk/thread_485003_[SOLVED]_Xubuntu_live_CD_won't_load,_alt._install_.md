---
title: "[SOLVED] Xubuntu live CD won't load, alt. install stops"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by GeorgeAD on 2007-06-26
Hi!

I'm trying to install Xubuntu 7.04 on an oldish computer (350MHz PII, 192MB). 

I've tried running the live cd, but that gets as far as the screen with the Xubuntu logo and the progress bar moving from side to side, at which point the bar stops moving. 
I'm pretty sure that the cd is okay, because I used it to install on a different computer. 

With the alt. install cd, I get as far as putting in the location/keyboard info, then the program detects the cd drive. That process seems okay - it gets to 100% and the grey box disappears. Now there's just a blue screen with a grey bar at the bottom. After a couple of minutes the Caps Lock and Scroll Lock lights on the keyboard start flashing. But that's it...

Any ideas please? 

cheers, 
George

---

### Post by GeorgeAD on 2007-06-26
More info:

If, after the lights start flashing, I press ctrl+alt+F2, nothing happens. But if, after the cd drive detection stage but *before* the lights start flashing, I press ctrl+alt+F2, I get to a console screen. 
If I wait a couple of minutes at that screen then the lights start flashing as before, and a load of info comes up whose last two lines are:

[  143.112117]  <0>Kernel panic - not syncing: Fatal exception in interrupt
[  143.130322]

---

### Post by GeorgeAD on 2007-06-28
If at the first menu I press F6 and type:

noacpi
nolapic

then the same thing happens, only this time the Kernel panic message is followed by: 

atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.

---

### Post by Bliepo32 on 2007-06-28
I had something like this. The problem turned out to be my overclocked videocard. Putting the clock back fixed it.

EDIT: at least, that is what I think it was.

---

### Post by GeorgeAD on 2007-06-28
Hi Bliepo, thanks for your reply. My video card is built-in (STB velocity 128); I searched the forum for that card and found someone with the same problem, but no solution. I've installed ubuntu 5.10 okay, it's just with the new version and xubuntu that it won't work...

---

### Post by GeorgeAD on 2007-06-28
That smiley face should be an 8!

---

### Post by Celegorm on 2007-06-28
I have no idea what the cause is, but I have had a similar problem with Xubuntu booting from the livecd on an old computer before. After a certain point in the bootup, it started spitting out a whole mess of errors, but after I waited a long time (half an hour?) it did eventually boot up and seem to work. I never did try to install it though.

---

### Post by GeorgeAD on 2007-06-28
Hi Celegorm, thanks for your reply, though I'm not sure if it's the same problem - I've left it for at least an hour to see if it would load, but nothing...

---

### Post by Celegorm on 2007-06-28
Ah, yea, that does sound like it's a different problem. If you already got Ubuntu to install on it, though, perhaps it might be less troublesome to install XFCE from there? I don't know if that might be problematic, or totally different than what you are looking for, but might be worth a try.

---

### Post by GeorgeAD on 2007-06-28
Yes, that was the other option, though I found I couldn't add repositories like I did before, so thought maybe it was going to be harder to update now 5.10 is a couple of releases old; also updating 3 times and changing from Ubuntu to Xubuntu desktop starts to sound like a lot of trouble, so it would be better to install from the latest Xubuntu cd (either live or alt.) if possible. I was hoping it would just be a matter of finding out why it wouldn't load and using the appropriate parameter - something like those acpi ones. I found them suggested on another thread, though I don't know what they do - I'm a bit out of my depth really.

---

### Post by GeorgeAD on 2007-06-29
I've tried various combinations of the cheat codes at:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and also some that I found for Knoppix, but it freezes in the same place no matter what (on the live cd).

---

### Post by oilchangeguy on 2007-06-29
why not try xubuntu 6.06 instead of 7.04.

---

### Post by GeorgeAD on 2007-06-29
Just tried that - same problem! 

On the live cd, the last messages (with 'quiet' deleted but no other changes) are:

Mounting root file system...
Running /scripts/casper-premount                              ok

then it stops, and the lights start flashing after a couple of minutes

---

### Post by GeorgeAD on 2007-06-30
last few lines before "kernel panic":

[<c03d77f5>] start_kernel +0x365/0x420
[<c03d7230>] unknown_bootoption+0x0/0x260
=====================
Code: 0f b6 54 24 07  [then a couple more lines of numbers...

EIP: [<c0263404>] ide_execute_command +0x94/0xx0 SS:ESP 0060:c03d3

<0>Kernel panic - not syncing: Fatal exception in interrupt



 (approximately - probably some mistakes copying it down)

---

### Post by GeorgeAD on 2007-07-14
Any ideas please?

---

### Post by GeorgeAD on 2007-07-31
Fixed it!

In case it's any use to anyone, the model name on the box is Gateway GP6-350, and the combination of codes that worked was:

noapic
nolapic
acpi=noirq
pci=noirq
irqpoll

That was enough to get the live cd working. But then I ran into a partitioning problem (known bug in XUbuntu installer I think) so used the alt. install cd, where the same combination of codes worked.

---

### Post by ub-newbie on 2007-08-03
Same solution worked for me.

Error Message = "Spurious ack on ISA0060 / Serio0.  Some program might be trying access hardware directly."

Solution =  At the boot options screen I typed, "live no apic no lapic acpi=noirq pci=noirq irqpoll".  The response I got was "unknown option - no irq", but it loaded.  (I don't know what all that means, I just type).

Sysem = PII 400, SB-16, Tyan Tsunami S-1846 MoBo, D-link NIC, Diamond video card (AGP) 

Loaded Xbuntu (I think it was Feisty Fawn).

---

