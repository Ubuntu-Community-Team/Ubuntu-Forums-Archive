---
title: "Ubuntu and Processor Upgrades"
date: 2007-09-23
forum: Apple PPC Users
---

### Post by MisterRik on 2007-09-23
I'm considering giving my PowerMac G4/466 (Digital Audio) a processor upgrade ([this one right here, to be exact](http://eshop.macsales.com/item/Other%20World%20Computing/MEG42M1200/)). While I don't anticipate any problems on the Mac OS X side, I thought I'd ask whether Ubuntu (Feisty Fawn) is going to have a problem with this.

Is there anything I should be aware of before installing this upgrade?

Thanks :)

---

### Post by ssam on 2007-09-23
should be fine.
same architecture, same chip type, just different speed.

almost everything is auto detected at boot in linux these days.

---

### Post by stmiller on 2007-09-23
2MB L3 cache! That will be a nice box.

---

### Post by MisterRik on 2007-09-23
> **stmiller said:**
> 2MB L3 cache! That will be a nice box.

Yeah, almost tripling my speed will be nice. I've had this G4 for about six years, and I've been falling behind when it comes to the latest software. I've been wanting to play World of Warcraft, but no chance of that with only 466 MHz (though I also have doubts about my stock video card), and a new Intel-based Mac is out of the question for my finances. Actually, I'll be happy if I can play Diablo II with all the video settings maxed out. I've never really understood why that game isn't smoother on my machine. My existing processor, video card, and RAM all exceed the "recommended" hardware requirements by at least a factor of x2, yet I still have to run the game in "software rendering" mode, with the various cool effects all turned off. Otherwise, the whole game bogs down and becomes unplayable.

Even Mac OS X (Tiger) itself is getting to be a bit too much for the hardware, which is one reason that I've installed Ubuntu. I'm now doing all of my Web-surfing, e-mail, and general computing stuff under Ubuntu these days, simply because it's "snappier", and only booting Mac OS X when I need to use certain software that I don't have for Linux.

Anyway, thanks for the reassurance that Ubuntu won't have trouble with the processor upgrade (I made sure to look for an upgrade that didn't require any kind of enabling software). I'll go ahead and order the upgrade today :)

---

### Post by seatea on 2007-09-24
I put the same processor in my PM G4 400mHz Gigabit about a year ago. It increased the speed of  Ubuntu significantly and the processor speed was recognized in the hardware profile without a problem. Mac OS X also runs much faster.

---

### Post by MisterRik on 2007-09-25
> **seatea said:**
> I put the same processor in my PM G4 400mHz Gigabit about a year ago. It increased the speed of  Ubuntu significantly and the processor speed was recognized in the hardware profile without a problem. Mac OS X also runs much faster.

Cool! Thanks :)

OWC says my order shipped today!

---

### Post by ssam on 2007-09-25
> **MisterRik said:**
> Cool! Thanks :)

OWC says my order shipped today!

be sure to let us know if it works

---

### Post by MisterRik on 2007-09-29
New processor arrived today! Installation was pretty straightforward. The only hitch was that I had to leave out one of the screws that holds the fan module in place atop the heat sink. These were extremely small screws, making them hard to hold onto while getting them into the holes. In addition, the screw holes closest to the rear of the machine  were kind of wonky, making it extremely difficult to get the screws in. To insert the screws on the rear side of the processor daughtercard, I had to remove my video card and all of my RAM in order to get the screwdriver in there. The reason I had to leave off the one screw was because, since it wouldn't go in all the way, it was blocking the nearest RAM slot. Now that I think about it, I had to leave off a couple screws when I installed my second hard drive, too. Couldn't get to them!

Anyway, neither Mac OS X nor Ubuntu appear to be having any trouble with the new processor. I'm enjoying my new 1.2 GHz! Now I just need to decide what I'll upgrade next. I need three things: more RAM (replace the existing 3 X 256 MB with 3 X 512 MB sticks), a bigger primary hard drive (30 GB seemed so big when I first got this machine ...) and a bigger, better video card.

---

### Post by walter_f on 2007-10-01
> **MisterRik said:**
> I'm considering giving my PowerMac G4/466 (Digital Audio) a processor upgrade ([this one right here, to be exact](http://eshop.macsales.com/item/Other%20World%20Computing/MEG42M1200/)). While I don't anticipate any problems on the Mac OS X side, I thought I'd ask whether Ubuntu (Feisty Fawn) is going to have a problem with this.


As the Digital Audio 466 is the first (and today, the "smallest") Power Mac G4 with a 133 MHz system bus, you will get considerably better results than, say, on an AGP G4 450 MHz that only has 100 MHz bus speed.

Expect to have a very nice machine :)

Regards,

Walter.

---

### Post by walter_f on 2007-10-01
> **MisterRik said:**
> New processor arrived today! Installation was pretty straightforward.

Anyway, neither Mac OS X nor Ubuntu appear to be having any trouble with the new processor. I'm enjoying my new 1.2 GHz! Now I just need to decide what I'll upgrade next. I need three things: more RAM (replace the existing 3 X 256 MB with 3 X 512 MB sticks), a bigger primary hard drive (30 GB seemed so big when I first got this machine ...) and a bigger, better video card.

If budget is in constraint, go for the maximum of RAM you can afford.
If not, start with the maximal RAM upgrade anyway.

Walter.

---

### Post by MisterRik on 2007-10-16
Sorry to resurrect a zombie thread, especially for a hardware issue.

I've had to uninstall the new processor and reinstall the original equipment.

Why?

Kernel panics. The processor upgrade worked beautifully for the first week or so, but then I started having kernel panics, both in Mac OS X and Ubuntu. Last night, the situation had degenerated to the point where I couldn't even boot the machine (into either OS). The kernel panics would come during bootup.

I suppose I've got a directory full of core dumps somewhere now ...

I dug out the Apple Hardware Test CD that came with my Mac and was able to "boot" from it. I ran the Extended Test, and that verified a problem with the logic board. So I yanked the processor upgrade and reinstalled the original processor, and I'm back up and running.

I've opened a support ticket with Other World Computing, so we'll see what happens from here.

---

### Post by roazena on 2007-10-17
Sounds like you did intelligent, thorough diagnostics. OWC is usually good folks, so keep us posted.

---

