---
title: "ASUS P6X58D Premium RAM issue"
date: 2011-10-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by christopher.wortman on 2011-10-28
I bought 6x 1G Crucial Ballistix Sport (supposedly supported A, B, C, D so I am suppose to be able to use all 6 channels)

I put it in, hard drive and everything went swimmingly, got Ubuntu 64 bit 11.10 installed, and I noticed I kept stubbing my toe on 4 gig of ram when processing high end stuff.

Intel XEON 3503 processor (The XEON series is well supported and I got the processor on ebay.) Now I did my research and for all accounts the processor *SHOULD* work. It does, everything seems to run along swimmingly. I don't have another 1366 processor just laying around to test this board.

DIMM 1 doesn't work right. Because of Intel ICH10 specifications, you need 2 sticks of ram and they work in tandum. I swapped each and every stick out, memtested them all and all the ram works.

Here is the really screwey part, when testing with all 6 sticks in, in memtest86 they show up, but only tests to 4097mb (I am guessing the 1mb is on the motherboard somewhere to load BIOS into.)

I have checked all the pins under the processor and none were bent. I installed a copy of Windows 7 64 in "demo mode" without a key just to see if it would work in Windows. (I work in a computer repair shop and want this to be my workstation running Ubuntu) I changed DRAM timings, and ich10 voltage steps, and even overclocked the processor for a few seconds to see if it would *kick start* the ram. (It worked on other builds as maybe the board needed a quick "burn-in") The ram works in other systems and it all tests out perfectly.

The OS works stabally registering only 4gig in process manager. I am highly doubting it is the motherboard not working, nor am I under the assumption that the ram doesn't like each other as they are all the same ram and I tested everything in another higher end system and they all workd. Sata 3, and Sata 6 are stable as a rock, so I am under the assumption that the memory controller on the processor is not functioning properly.  Right now I am running in failsafe but it doesn't seem to make a difference.

Has anyone else with this board had the same issue and been able to resolve it? Is there something as far as processor in the BIOS that I could change to get it to recognize that I have all 6 gigs? I am going to head to my local puc shop and see if he would be gracious enough to lend me a copy of UX Burn-IN (a 75 dollar CD) Other than that I am at a loss, is there a free as in gratis thing like UX that I don't have to borrow or pirate? I am really in need of help. Thank you.

---

### Post by christopher.wortman on 2011-10-28
I ran CPU Burn in and all the registers look fine, I also ran memtest86 and it tests up to 5120mb of ram, and it all passed with flying colors (I made some progress but not much) Any help at all would be greatly appreciated. :)

---

### Post by christopher.wortman on 2011-10-28
alright I threw it all back together this morning, its stable as I suppose, I was hoping someone would have any information regarding this :-\

---

### Post by jmate24 on 2011-10-30
it may because you are using a 32bit version of ubuntu and not the 64bit version.

---

### Post by christopher.wortman on 2011-10-30
> **jmate24 said:**
> it may because you are using a 32bit version of ubuntu and not the 64bit version.

No offense but did you even bother to read the entire post? Or just post what you think is an answer? 

> 
I put it in, hard drive and everything went swimmingly, got Ubuntu 64  bit 11.10 installed, and I noticed I kept stubbing my toe on 4 gig of  ram when processing high end stuff.

second line my friend...

Moving on. I tried even increasing voltages here and there yet still nothing. I ran a full UX and UX sees and tests all 6 gig of ram as it bypasses BIOS, the processor tests out keenly which leaves me to believe ASUS is a sucky manufacturer of boards and BIOS...

---

