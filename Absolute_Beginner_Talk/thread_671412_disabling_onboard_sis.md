---
title: "disabling onboard sis"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by yuffie8 on 2008-01-18
hey, im not sure if this should go in here but i have an oboard graphics SiS (device: 5513 [IDE]) and i want to be able to disable it so i can slot in an old GF FX5200 DDR that i have been given. Is this possible ? I looked through the bios but i couldnt find anything related and dont know enough about it all.

My RAM is DDR2, is this a problem for the card ? 
The motherboard is a AMD Sempron 2400+

Any help would be appreciated, cheers if you can help a noob out!

---

### Post by Paul820 on 2008-01-18
When you put the graphics card in the onboard should get disabled by default.

---

### Post by yuffie8 on 2008-01-18
hey, thanks for the quick reply, i just put the card in ... turned the comp on and the screen is blank, the monitor is on (light green not amber if that means its detecting it i dont know ...), hmm. It doesnt show anything i cant go into bios or anything.

---

### Post by hardyn on 2008-01-18
did you move the monitor cable over to the new video card? thought i would check.

make sure the default video port is AGP (or PCIE) not onboard.

---

### Post by yuffie8 on 2008-01-18
> **hardyn said:**
> did you move the monitor cable over to the new video card? thought i would check.

make sure the default video port is AGP (or PCIE) not onboard.

I had moved the monitor cable over yes (dont worry about asking the most basic questions and sounding insulting, i am compltetely new to all this so its completely reasonable!).

Ok so to do that im in the bios right ? (i took it out - im on a laptop so i can keep online also) ... ok i might have just done that, ill update in 2 mins lol

---

### Post by yuffie8 on 2008-01-18
ok it didnt work ... but i heard the usual beep through the speakers ... im gona grab something to eat so back in a bit, cheers for helping tho guys

---

### Post by yuffie8 on 2008-01-18
ok so im back, as i say that didnt appear to work.. so im in BIOS 
Resource configuration
Primary graphics adapter - agp

am i on the right track ? after i selected that i put the graphics card back in, booted up and the screen went black but with the green light on.

bumpity bump bump ... if this doesnt get any responses ill leave it as generally i am quite pleased with how my ubuntu is working :)

---

### Post by yuffie8 on 2008-01-18
ok, so editing the message didnt bump it :( so here goes

---

### Post by RomeReactor on 2008-01-18
Hi. Have you tested this card in another machine (or windows, if you dual-boot)? It's possible the card doesn't work. Also, try booting in Safe Mode (or Recovery Mode, I don't remember) and see if the display works then.

---

### Post by LowSky on 2008-01-18
OK im really confused...for good reason
AMD semphron at 2400+ should be using DDR not DDR2, DDR2 should even fit into the same slots as DDR they have different amounts of pins. Is  it a AMD semphron64? then that would be different. but that shouldn't effect the graphics.. what i need is to know how old is the computer to begin with. Please could you post the name and make of your presumably mATX motherboard, it might help me troubleshoot for you.

Second an FX5200 is AGP, which could be the wrong slot on your motherboard as it could be PCI-express, both slots look and fit about the same. The card you got could be broken or your not enabling the port correctly in BIOS. The card should be installed before you enable AGP mode for grahics. There should also be an option to turn off the onboard graphics. Also turn off anything that say shared video RAM. On some motherboards you might not have this option but some have jumpers on the motherboard itself to turn off onboard graphics.

So if we know the motherbard make and model, or maybe even the name brand we could help more.

---

### Post by Efros on 2008-01-18
I've just been through this on a machine with an onboard graphics card, in the BIOS I had to make sure that the PCIex was the first graphics device and also select 0 Mb for the shared memory/frame buffer for the onboard graphics card. This latter action actually disabled the card. Once I had done this Ubuntu configured the installed 7300GT correctly. Took me 2 days to figure it all out, yeah I know I'm slow.

---

