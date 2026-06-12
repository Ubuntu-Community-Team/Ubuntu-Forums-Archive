---
title: "Dual booting and other computer configurations"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by ACF1 on 2008-02-19
I now have 2 older boxes.  I have 4 hardrives that are all moderately sized.  And 3 CD drives. One box has a much better processor then the other.  What would be a good way to configure all this into one computer?  Crazy, I know, but is there any way to hook the 2 computers together and use them both?  I want to dual boot Win XP and Ubuntu.  Should I just put as much stuff into 1 of the boxes as I can?  How about partitioning?  I am looking for ideas on what I should do with the computers and the best options.  Thanks.

---

### Post by Paqman on 2008-02-19
Well, what are you planning on doing with them? 

You could put all the best parts into one box, use that as your main PC, and turn the other one into a file server/NAS/Seti@home box/paperweight.

---

### Post by Fred_E _krugar on 2008-02-19
lol I like the paperweight. Especially if it is windy in your location.

---

### Post by Therion on 2008-02-19
My two-cent's:

Take the case with the best CPU/Mobo combination.  Install the two best hard drives and the best single optical drive of the lot.  No such thing as "too much" RAM either.

What about video?  Hopefully you can pull a discrete solution (e.g. an actual PCI/AGP/PCI-e video card) from one of the boxes and install that.  

If you're going to dual-boot, install Windows and then Ubuntu on drive A (partition as you need/see fit) and use Drive B for data storage and backup duty unless you wanna get all fancy and set up a RAID config.  In my opinion, humble as it is, RAID 0 configs really aren't worth the time, trouble, etc..  A secondary hard drive though, isolated and OS-free, is an absolute must-have.  I wouldn't have a system these days with a single hard drive.

---

### Post by ACF1 on 2008-02-19
How do I tell which motherboard is better?  One of them has way more slots to put stuff in then the other.  And can I take one processor and put it on the other board? 

Thanks.

---

### Post by ACF1 on 2008-02-20
I don't know what kind of motherboards I have, but the possessors are an Intel Pentium III and an Intel Celleron (I think).  Would they be compatible?

---

### Post by Therion on 2008-02-20
> **ACF1 said:**
> I don't know what kind of motherboards I have, but the possessors are an Intel Pentium III and an Intel Celleron (I think).  Would they be compatible?This is one of those "It All Depends" situations.  Without knowing the make and model of motherboard, specifically, and the specifics of the processors themselves, it would be impossible to say if any particular combination is going to be compatible.  I'd suggest leaving the processors where they are, since pulling them and remounting them in new motherboards would A) be a pain in the butt and B) may result in compatibility problems.  Too much effort, to little too gain.  Further, I'm no fan of the Celeron processor, but that's just me, and for routine desktop type stuff, it can be an entirely adequate little chip.  Again, It All Depends.

In short though, without being able to pin down the technical specs of the hardware in question, it will be impossible for anyone to give you any good advice about what to do.  If you can assemble bootable machines, then you could start to identify parts, and specs on those parts, via DXDIAG, SiSoft Sandra, the Device Manager, etc.  But without that information it's all a guessing game.

---

### Post by ACF1 on 2008-02-20
> **Therion said:**
> This is one of those "It All Depends" situations.  Without knowing the make and model of motherboard, specifically, and the specifics of the processors themselves, it would be impossible to say if any particular combination is going to be compatible.  I'd suggest leaving the processors where they are, since pulling them and remounting them in new motherboards would A) be a pain in the butt and B) may result in compatibility problems.  Too much effort, to little too gain.  Further, I'm no fan of the Celeron processor, but that's just me, and for routine desktop type stuff, it can be an entirely adequate little chip.  Again, It All Depends.

In short though, without being able to pin down the technical specs of the hardware in question, it will be impossible for anyone to give you any good advice about what to do.  If you can assemble bootable machines, then you could start to identify parts, and specs on those parts, via DXDIAG, SiSoft Sandra, the Device Manager, etc.  But without that information it's all a guessing game.

So which motherboard do you think I should go with?  One of them has more slots and stuff, but the smaller processor (733 mhz) and windows 98 was natively installed on it.  The other motherboard natively had XP.  It has less slots and stuff, but a 1.4 ghz processor.

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> So which motherboard do you think I should go with?  One of them has more slots and stuff, but the smaller processor (733 mhz) and windows 98 was natively installed on it.  The other motherboard natively had XP.  It has less slots and stuff, but a 1.4 ghz processor.


Go with the 1.4Ghz processor. How much RAM do you have?

---

### Post by ACF1 on 2008-02-20
> **Duck2006 said:**
> Go with the 1.4Ghz processor. How much RAM do you have?

That board has only 2 memory slots, so the most I can get in it right now is 256 (that is, 2 128s).  But I am able to get more memory (buy bigger memory things (what are they called?)).

---

### Post by Therion on 2008-02-20
Definitely stick with the 1.4Ghz processor/motherboard combo for this and yes, you can get larger memory modules for the motherboard if you want.  You don't HAVE to fill both slots of course, unless you want to for some reason, so I'd probably look for a deal on a single 1GB RAM stick and call it good.

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> That board has only 2 memory slots, so the most I can get in it right now is 256 (that is, 2 128s).  But I am able to get more memory (buy bigger memory things (what are they called?)).

Is it onboard video? If so then you will need more than 256Mh of ram, you will have to look at the sticks to see what type it is ie PC100 or PC133 or PC2100 or ect.

---

### Post by ACF1 on 2008-02-20
Next question.  The board with the bigger processor had an integrated sound and graphics card.  Can I install a stand-a-lone graphics and sound card?

---

### Post by Therion on 2008-02-20
> **ACF1 said:**
> Next question.  The board with the bigger processor had an integrated sound and graphics card.  Can I install a stand-a-lone graphics and sound card?
Yes, assuming you have at least one PCI slot for a sound card and an AGP, PCI or PCI-e slot for a video card.  Can you ascertain the make and model of the motherboard?  It's usually printed right on the board itself, somewhere.  We could use that information to get the detailed specs on your board, which would help a LOT.

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> Next question.  The board with the bigger processor had an integrated sound and graphics card.  Can I install a stand-a-lone graphics and sound card?

Yes you can you have to go into the BOIS and turn of the integrated sound and graphics, and then you can use stand-alone cards. The card for sound will be a PCI and for the graphics it depends on if you have a AGP slot or you will have to use a PCI card.

---

### Post by ACF1 on 2008-02-20
Also, the good board currently has ide cables with only one hook up on them (that is, no slave hook up).  Can I take the ide cables from the other box that have both slave and master hookups and put them on this board (the one with the good processor)? I want to be able to have 2 hardrives and 2 cd drives.

---

### Post by Therion on 2008-02-20
> **ACF1 said:**
> ... Can I take the ide cables from the other box that have both slave and master hookups and put them on this board (the one with the good processor)? I want to be able to have 2 hardrives and 2 cd drives.
Yes you can.  Just be sure the power supply is up to the task; two optical drives are going to suck down some serious wattage.
In point of fact, I'd suggest you install one, *good*, DVD burner and leave it at that.  Having two hard drives is an excellent idea, but two opticals?  IMO, **not** such a great idea unless you have some compelling reason for installing two that I'm not aware of.

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> Also, the good board currently has ide cables with only one hook up on them (that is, no slave hook up).  Can I take the ide cables from the other box that have both slave and master hookups and put them on this board (the one with the good processor)? I want to be able to have 2 hardrives and 2 cd drives.

Yes you can take the cables from the other system and use them in this one ok.

---

### Post by ACF1 on 2008-02-20
I looked all over the motherboard and I can't figure out what kind it is.  Though it does have to stickers with a bunch of numbers on them.

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> I looked all over the motherboard and I can't figure out what kind it is.  Though it does have to stickers with a bunch of numbers on them.

Try doing a search on a search engine of the numbers that you find on the MB ie if it has say MB-145 ext, for more information.

---

### Post by Therion on 2008-02-20
The make and model shouldn't be that hard to ascertain.  [This pic](http://www.escotal.com/Images/computer/motherboard.jpg) shows a motherboard.  The model number shows up between the letters "S" and "T" (it looks like P5K3 Deluxe) and the make is "Asus", as is shown under the letter "R" in that pic.  That's the sort of thing you're looking for.  Unfortunately, the information could be anywhere on the motherboard. 

But tell me this...  Where did these motherboards come from?  Did you pull them out of "off the rack" systems, like old Dell PC's or something?  If you did, we might do better Googling that information, since the boards may be proprietary.

---

### Post by ACF1 on 2008-02-20
Perhaps this number is it?   aa a51507-805

---

### Post by Duck2006 on 2008-02-20
> **ACF1 said:**
> Perhaps this number is it?   aa a51507-805

That shows that it is a gateway board.

[http://www.ask.com/web?q=aa+a51507-805&search=search&qsrc=0&o=0&l=dir](http://www.ask.com/web?q=aa+a51507-805&search=search&qsrc=0&o=0&l=dir)

---

### Post by ACF1 on 2008-02-20
The boards are what came in the boxes.  The one with the good processor is a Gateway.  I don't know what kind though because it was given to me.  And I tried and tried but could not find out what kind of gateway it is.  But it must be fairly new because it had windows xp on it.

---

### Post by Duck2006 on 2008-02-20
Has gateway's website given you anu info on it at all?
Was there any numbers on the box that the board came in?

---

### Post by ACF1 on 2008-02-20
> **Duck2006 said:**
> Has gateway's website given you anu info on it at all?
Was there any numbers on the box that the board came in?

It must be an odd ball box and board or something, because I couldn't find anything out about the box (I think I searched every number on the box).  And also I can't find out much about the motherboard, other then that it appears to be a Gateway.

---

### Post by Therion on 2008-02-20
From what I've been able to ascertain, the board was manufactured by HP/Compaq for Gateway computers.  It *appears* there is no AGP slot, but I find no reference *at all* to the presence of PCI slots.  Do you know what PCI slots look like?  Because without them you won't be able to install a video card or a sound card, and if you want to install both of those, you're going to need two PCI slots.  Memory, I think we can assume is standard, 186-pin DDR, but if worst comes to worst we (meaning "you") can always count.

---

### Post by ACF1 on 2008-02-20
> **Therion said:**
> From what I've been able to ascertain, the board was manufactured by HP/Compaq for Gateway computers.  It *appears* there is no AGP slot, but I find no reference *at all* to the presence of PCI slots.  Do you know what PCI slots look like?  Because without them you won't be able to install a video card or a sound card, and if you want to install both of those, you're going to need two PCI slots.  Memory, I think we can assume is standard, 186-pin DDR, but if worst comes to worst we (meaning "you") can always count.

It has 3 PCI slots.  And the memory slots are the same as my other box.  I think it is just standard DDR memory.

---

### Post by Therion on 2008-02-20
> **ACF1 said:**
> It has 3 PCI slots.  And the memory slots are the same as my other box.  I think it is just standard DDR memory.
Well there you go!  Install the PCI video card and sound card of your choosing as well as some additional RAM and you should be rocking and rolling.  Keep an eye on the power supply though, if you intend to soup this box up with dual hard drives and dual optical drives.  Those off-the-rack systems are NOTORIOUS for using crappy, barely-adequate, power supplies; and in my experience when one of those crappy, barely adequate power supplies decide to sing their Swan Song, they quite often like taking the mobo along for the (eternal) ride.

---

