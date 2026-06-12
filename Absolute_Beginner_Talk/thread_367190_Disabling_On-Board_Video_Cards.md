---
title: "Disabling On-Board Video Cards"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Funk Soul Brother on 2007-02-21
Gang,

Has anyone ever tried to disable an on-board video card in favour of a new AGP card?

I am trying to get Edgy installed, but the Intel 82845G on my Intel 845G Motherboard will only give me 640x480 resolution (believe me, I've spent hours reading posts and trying stuff).

Since it looks like this crazy card won't run x-server - I'm looking at spending cash (and I'm a cheap Scotsman) to get an Nvidia - like a GeForce 7600GS or a 6200LE.

Please help me. I don't want to polish a gun barrel with my tongue over this.

---

### Post by Maestro23 on 2007-02-21
Should be able to do it thru the BIOS of your computer.  That is what I did on my Gateway.

---

### Post by Funk Soul Brother on 2007-02-21
Maestro23,

Thanks - will try. The box is in the shop getting a memory upgrade.

I read that these types of motherboards automatically detect a card in the AGP slot and shut down the on-board. Does that sound right to you?

---

### Post by Veggieb0i on 2007-02-21
Well, if you already have the AGP card, you'd just go to your motherboard settings (Pressing "DEL" when the black screen shows right after you turn the computer on).
On my particular menu, the setting you're looking for would be "Init display first", but just look around if that one isn't there. But, you absolutely must have the AGP card in the computer already, or you'd have to reset the BIOS to see anything!
It has happened to me; it sucks.

---

### Post by HereInOz on 2007-02-21
The on-board chip should be disabled by the system when you plug in the AGP card.  If not, then you would need to look through your BIOS set up and see if there is a facility to turn it off.   Usually not though.  More so you will find that when you plug in the AGP card, and the system no longer sees, nor wants to use, the on-board chip.  

You will probably notice that the available memory goes up, as the RAM put aside for the on-board chip is released for proper RAM duties.

---

### Post by ed-j on 2007-02-21
Lurking in your CMOS you will find something like "onboard device function", this will give you options for onboard VGA, PCI, AGP or PCI-E. Chose which one you want, Press F10 and "Y" to make the changes. If your card is connected, it should work. If not, try rubber bullets, they are much more considerate to ambulance crews: Not as much mess you see.

Good luck!

The advice from HereInOz is also spot on! Dailema, you know, the Welsh Dali-Lama.

---

### Post by Funk Soul Brother on 2007-02-21
Right on. I will try this stuff out when I get the box back tomorrow or so. G'nite and thank you all.

---

