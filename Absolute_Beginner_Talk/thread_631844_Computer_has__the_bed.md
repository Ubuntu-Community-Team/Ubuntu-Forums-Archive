---
title: "Computer has **** the bed"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by pooper on 2007-12-04
Ok it all started... I was using ubuntu and kubuntu quite happily, until I had to install windows! I had to install windows because of my uni only having windows machines and I needed to work between the two. Anyway, I sorted out all the partitioning and got windows installed and sorted out GRUB. Then in windows (xp) I kept getting blue screen of death telling me IRQL_NOT_LESS_OR_EQUAL and a load of jibba jabba. I blamed this on my graphics card & driver, because I started getting the error once I installed the GFX card driver! And then eventually windows really messed up and now gets the blue screen as soon as it loads.
 It gets worse... I decided to leave windows for the moment until i sort the GFX and went into kubuntu. I was using the add remove programs to do just that and then kubuntu decides to restart. And now, nothing loads up. not ubunutu not kubuntu and not windows. I get past the loading screens in all of them and then they crash. I've taken the pc to pieces and reassembled... still nothing! So I've tried using a gparted live cd and that doesn't even want to know! I go into force vesa mode and i get crc error. :confused::confused::confused: extremely :confused::confused::confused:
Ive looked at my bios, CPU temp is 52*. im guessing thats ok?
help!?

---

### Post by SOULRiDER on 2007-12-04
Try using a live CD and check your memory for issues. It sounds like a hardware problem to me.

---

### Post by pooper on 2007-12-04
I ran memtest earlier and got no errors. Also just tried loading into ubuntu again, the default and that doesn't even come to a loading screen now. get a black screen of text i believe saying application error, command line style. will try live cd now.

---

### Post by pooper on 2007-12-04
ok ran ubuntu live cd, which worked before... in safe graphics mode and am presented with 

ran out of input data

 -- system halted

---

### Post by SOULRiDER on 2007-12-04
I think ti must probably be a hardware problem. See if you can borrow an empy drive from someone and install Linux on it. See if everything runs or if it doesnt.

---

### Post by pooper on 2007-12-04
why would it run off a clean installed drive if it doesn't run off the ubuntu live cd, or gparted live cd? the only thing i can get to run at the moment is memtest.

---

### Post by pooper on 2007-12-04
Pleeeeaase anyone out there ?
I'm off to bed for now as it's 03:42 in UK, suggestions appreciated :)

---

### Post by pooper on 2007-12-05
ok so now, I've tried unplugging the hard drives and running the live cd with only the cd drives installed. It doesn't work .... same error, something like

no input data

crc error



!? :S  I'm running memtest now again as it the only thing that runs :D but can i just ask, what mem does memtest actually test, is it just the ram modules or everything like cache and graphics card ???

I also tried installing windows off the windows install disk (when HD was installed) and even that doesn't work, it barely even starts infact.

---

### Post by mcduck on 2007-12-05
> **pooper said:**
> 
!? :S  I'm running memtest now again as it the only thing that runs :D but can i just ask, what mem does memtest actually test, is it just the ram modules or everything like cache and graphics card ???

Just the RAM. It's also important to know that running memtest once doesn't tell you anything. It should be run for long time, at least over night, as memory errors often start appearing only after some stress on the memory.

---

### Post by philinux on 2007-12-05
[http://en.wikipedia.org/wiki/Cyclic_redundancy_check](http://en.wikipedia.org/wiki/Cyclic_redundancy_check)

Sounds like some hardware died.

---

### Post by pooper on 2007-12-05
memtest, so anyone know what this means ? (see attachment) 
I'm guessing RAM has had it

---

### Post by asmiller-ke6seh on 2007-12-05
looks like a chunk of memory bought the farm - just as it was previously postulated. :(

---

### Post by scrooge_74 on 2007-12-05
Yep, go get new RAM that one just had it, in any case you should check that your power supply is not having some issues which results in hardware to start dying out slowly one at a time.

did you had any power flux with the PC on? I have that kind of issue a couple of times

---

### Post by pooper on 2007-12-05
I don't know what you mean by power flux? 
Hmm i did replace ram a little while ago, and got the whole thing running ubuntu, then my psu started making horrible noises so i also replaced that not so long ago, although i must admit i bought a fairly cheap one.

---

### Post by scrooge_74 on 2007-12-05
What I meant by a power flux, sometime the current will ahve spikes and that will damage things, if you had already replace ram a little while ago I strongly suggest you check the power supply or change it before it takes out something more expensive.

How old is the PC or how old is the power supply those things die after a couple of years

---

### Post by philinux on 2007-12-05
When you say cheap power supply, how cheap is that.

It really can screw you're rig if you go cheap.

---

### Post by pooper on 2007-12-05
pc is a few years old now, bits and pieces changed now and then. The PSU is probably a few months old. I have 2 sticks of ram 512 and 256 I'll fiddle about with them and see if i can pin point one of those then I think i've got some mobos in the loft which might work, I'll try them. If not I guess its the processor or PSU. I haven't mentioned gfx card because I've tried 2 and getting the same error.
thanks for all the suggestions I will re post when I've investigated more.

---

### Post by pooper on 2007-12-05
oh yeh cheap, the cheapest i could find locally at £20 400w

---

### Post by pooper on 2007-12-05
also if this is any help this is an error I kept seeing in windows when that was loading...
I blamed drivers or gfx card.

---

### Post by shamasis on 2007-12-05
If memtest is fine and simultaneously u cannot boot using ur hdd, it implies memory is OK. As, no stress is required to boot the OS.

Your RAM maybe fine. Your graphics card may have gone kaput! If command line booting is fine, tthen gfx card may be the culprit.

try booting into command-line mode.

With windows, does Safe mode boot works? If yes, then i guess ur gfx card is the culprit.

---

### Post by LowSky on 2007-12-05
> **pooper said:**
> oh yeh cheap, the cheapest i could find locally at £20 400w

so thats about $45 american?
that isnt really that cheapto some, but in my opinion a power supply should be as heavy as a brick and you shouldn't be able to see completely thought the fan holes, the less stuff inside the crappier the PS is. A good one cost roughly $80+ american

Also you're processor running over 50'C on a constant basis is a bad thing. Shouldn't be any higher than 45'C on a full load (100% processing)

Your IRQ blue screen is a motherboard issue, your RAM maybe fine. It seems that your computer cant send data pakets the right way because of failing  Circuit line, caused by  bad power lines... in your BIOS does it list the the voltages? could you post them?

---

### Post by PmDematagoda on 2007-12-05
Actually, a temperature of 56C is not that bad, mine is worse, it ran(And is still running) for one year at an average temperature of 59C. So provided that your mainboard and processor are built well, you should not face many problems.

But it is always good to maintain the processor temperature at a low level, mostly because the sound produced by the fans is simply too much to bear:mad:.

---

### Post by shamasis on 2007-12-05
> **pooper said:**
> memtest, so anyone know what this means ? (see attachment) 
I'm guessing RAM has had it
[http://msdn2.microsoft.com/en-us/library/ms793589.aspx](http://msdn2.microsoft.com/en-us/library/ms793589.aspx) exactly what u need!

---

### Post by pooper on 2007-12-05
Thanks for all the help people, 
the microsoft link confirms what i thought originally, its a bad gfx card driver. But things since then must have got worse. 
> 
Your IRQ blue screen is a motherboard issue, your RAM maybe fine. It seems that your computer cant send data pakets the right way because of failing Circuit line, caused by bad power lines... in your BIOS does it list the the voltages? could you post them? 
I've just freshly turned on the computer and voltage / temp results are in attachment.

Memtest doesn't run now i've discovered i jumped the gun. I get unexpected interrupt, type Inv_Op

Also I've tested 2 gfx cards in the system and get same problem

---

### Post by pooper on 2007-12-05
oh and btw, in that screen shot all I have plugged in is 2 cd drives on the primary ide no HDs installed because I wanted to eliminate them as a problem and use live cds. Also no PCI cards, unplugged front usb on case so its all very basic.

---

### Post by atlfalcons866 on 2007-12-05
> **PmDematagoda said:**
> Actually, a temperature of 56C is not that bad, mine is worse, it ran(And is still running) for one year at an average temperature of 59C. So provided that your mainboard and processor are built well, you should not face many problems.

But it is always good to maintain the processor temperature at a low level, mostly because the sound produced by the fans is simply too much to bear:mad:.

my sempron gets to 56C under heavy load. what cpu do you have?

---

### Post by pooper on 2007-12-05
Athlon xp around 2ghz i think...

---

### Post by atlfalcons866 on 2007-12-05
AMD processors tend to get hot.

---

### Post by Bigbird999 on 2007-12-05
The screenshot  of his failed memtest shows it to be an AthlonXP at ~2000 Ghz (not sure which one, maybe an XP2800+) .  These XP CPUs normally run 50+deg, and hotter when loaded.  no problem.  

Those socket A mobos with the XP CPUs are pretty robust, not to say it couldn't be a failed mobo or CPU, it happens, but it could also be something really minor that can be inexpensively fixed  I have several of these beasts an have yet to encounter a failed mobo/cpu but lots of other hardware has failed.

Is this processor overclocked by any chance?  Which mobo is it?  Does it have onboard video in addition to the GFX?  If so you could try removing the GFX card and seeing if it will boot to the bios.  Also removing the video card and reinstalling it in a different PCI slot might work.  Will it POST with just one stick of memory installed?

Try running memtest with only a single stick of memory installed to try an isolate the bad stick.   

If you can post more specific system specs I might be able to help you diagnose the problem or point you

---

### Post by Sef on 2007-12-06
> Try running memtest with only a single stick of memory installed to try an isolate the bad stick. 

That's a good idea.   I had memory problems and did that.  Turned out to be the memory module unit on the motherboard.

---

### Post by pooper on 2007-12-06
yeh I've ran memtest with 3 different sticks of ram, I've tried 2 different mobos, psu is pretty new.
mobo is aopen via kt600 ak77 600gn amd athlon xp.
oh yeh sorry forgot to mention the gfx card is agp slot. 
I'm fairly confident its a motherboard problem so I have a few in the loft which might still work I'll have to dig them up and try those to see if error persists. 

thanks for all the help


Edit; that should be I've tried 2 different gfx cards, not mobos.

---

### Post by pooper on 2007-12-10
Ok finally got up into the loft and fished out another motherboard... Problem solved :D

---

