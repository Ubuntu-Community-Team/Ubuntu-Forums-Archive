---
title: "I thought my BIOS chip was shot, but it doesn't seem so simple"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2008-01-29
i thought the BIOS chip was shot on my Acer AS5672WLMi laptop, since it would boot without the keyboard or mousepad functioning, the camera would give weird errors saying it "would perform faster if it were plugged into a usb 2.0 port" (this was on XP, and it's an internal camera). i ran MemTest86+ and it ran for two days without an error, but every single time (even now, when it seems fine, other than the battery holding absolutely no charge) i change the parameters to include all the BIOS memory i get this:

[IMG]http://img175.imageshack.us/img175/7275/00005un7.jpg[/IMG]

notice it has only ran for five seconds, with 5120 errors. this is the result every time i run the test, no matter if the computer is from a cold boot or if it's been running for several hours.

i got another hard drive (WD 250 gB, i think it's a Scorpio) and installed feisty, but had the same problems. i shelved the laptop using it as a glorified container for the working parts inside (i was planning on getting a new IBM with a small HDD and barely any RAM and just upgrading from my "broken" laptop)

i was bored a few nights ago and plugged in the "broken" Acer and it started right up, but it said no OS found (i think i reformatted the entire drive into ext3 after i gave up installing an OS to leave a clean drive). i installed Gutsy and it has been working fine, but now i am worried about the BIOS. is it just a ticking time bomb?

---

### Post by Shazaam on 2008-01-29
I have an old laptop with a completely dead/unchargable battery. If I leave the battery in while it's (the laptop) on ac power the laptop has problems similar to what you have. Try running it with the battery out and your power settings set in the bios to ac power and see if it has problems.

---

### Post by Sonic Reducer on 2008-01-30
no change at all, 5 seconds in with ~5100 errors with the battery unplugged

---

### Post by tgalati4 on 2008-01-31
You could try replacing the on-board battery.  This will be difficult, and you may find that the BIOS is still flakey.  Can you flash it with a newer version?

---

### Post by Sonic Reducer on 2008-01-31
how would i do that? i've tried to open up my laptop, but i haven't ever seen the battery (not that i've ever been looking for it, so i might have seen it dozens of times lol)

have any clues where i might find it?

---

### Post by Shazaam on 2008-01-31
The bios battery for my old Compaq is behind a plate on the bottom; yours is newer so it might be under the keyboard.

---

### Post by Sonic Reducer on 2008-01-31
how do i take that off?

---

### Post by Sonic Reducer on 2008-01-31
so i found the BIOS battery i believe, it was under the main plate of my laptop, but it was not in a socket like how desktops BIOS battery is kept. it was shrink-wrpped with two inch-long leads twisted and connected to the motherboard. 

[IMG]http://img239.imageshack.us/img239/2001/0130082340tr2.jpg[/IMG]

the label was 031??06, there was one or two numbers obscured by the blue dot, i'm not even sure how many numbers were obscured. is this a standard battery?

---

### Post by bigken on 2008-01-31
Its the cmos battery gone dead dont worry too much get a new one from ebay 
when these die you get all sorts of errors which amount to nothing bad checksum errors ect

---

### Post by Sonic Reducer on 2008-01-31
are you sure its the battery?

---

### Post by bigken on 2008-01-31
does the machine loss the date and time if you pull the power and normal battery
if it does its the cmos battery

---

### Post by Golem XIV on 2008-01-31
Did you try checking the memory physically?  I mean, replacing the memory SODIMM board?  If your laptop has 2 memory SODIMMs, try removing one and running the diagnostic, then put it back in, remove the 2nd one and run the diagnostic.

---

### Post by tgalati4 on 2008-02-01
Take a voltmeter and measure the voltage across the battery leads.  These batteries are soldered into the motherboard and require some effort to replace.  Not difficult if you know what you are doing.  You should probably get 3.6 VDC for a good battery.  2.8 VDC for a bad battery.  The laptop should be unplugged when testing, because sometimes the battery is rechargeable and not a lithium ion cell.  If rechargeable, you will get 4.2 VDC when wall-powered, and perhaps 2 VDC after a few hours unplugged.  Rechargeable batteries die after a few years.

---

### Post by Sonic Reducer on 2008-02-01
> **bigken said:**
> does the machine loss the date and time if you pull the power and normal battery
if it does its the cmos battery

i left it unplugged for 8 hours without a battery in, it still kept the date and time

---

### Post by bigken on 2008-02-02
> **Sonic Reducer said:**
> i left it unplugged for 8 hours without a battery in, it still kept the date and time


well its not the cmos battery 

I think you probablys had a bad cecksum error

---

### Post by Sonic Reducer on 2008-02-02
> **bigken said:**
> well its not the cmos battery 

I think you probablys had a bad cecksum error

can those be fixed?

---

### Post by bigken on 2008-02-02
to fix cecksum errors all you need to do is short  or remove the cmos battery but dont bother if the pc is working

---

