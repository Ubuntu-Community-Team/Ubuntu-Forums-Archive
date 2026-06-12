---
title: "Is it Software or Hardware?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-06-21
Okay, the condensed version is this:

The soon-to-be Ubuntu computer died a rather unusual death - hard drive failed in a very strange way.  It did (and still does) make a noise very similar to a car alarm whenever it's powered on.  (Basically it goes "BOOOooop" starting high pitched and then decreasing, tone lasts about 1-1.5 seconds and repeats every 15-20 seceonds.)  Shortly after this my work PC died and had to have the video card and power supply replaced, these parts were then cannibalized from the Ubuntu-to-be computer.

Since that hard drive and it's XP install are almost certainly a total loss, I decided to use the onboard video, a repaired power supply, and a cheap 20 gig hard drive to bring that computer back to life in Ubuntu glory as a test bed for a possible network-wide shift.

When I turn the computer on it refuses to output video at all (since it used to have a GeForce 4 installed), so I reset the CMOS.  If there's a better way to turn the onboard video back on, I couldn't think of it and I was getting tired at this point.

So now everything seems to be okay, except for the annoying problem that it takes for-freakin-ever for the thing to POST.  I pop in my 6.06 Live disc and let her rip.  Well, I wait and wait and wait for her to rip.  But it won't.  I'm getting some kind of error about the kernel flipping out before I get any graphics of any kind.  So I push F1, and push all the other F-keys and say a few F-words.  Then I read a bunch of stuff on the Support section here and decide I'm going to download 7.04 instead.  I burn that, pop it in, and after a few glaciers shift the CD boots up and everything looks great.  I whack "Install", answer the questions, and reflect to myself how positively this whole thing compares with your standard Windows install.

When informed that I can restart or continue using Live, I restart and pop the disc out as prompted.


Here's where Spektyr entertains the notion of placing his rather shaggy cranium through the wall.  I went into BIOS and switched my boot options to the standard order (Floppy, HDD-0, CDROM).  What's the computer do?  Try to boot from CD and then whine because I don't have a system disc in it.  So I switch all my boot order to HDD-0.  It still demands a boot CD.  So I put the Ubuntu CD back in, boot it up, and then select "boot from first hard drive" from the menu.  It tells me that the hard drive won't boot.  So I boot up into Live and take a look at the drive.  It looks perfectly fine to me, but then I've never actually seen an Ubuntu installation.  It's a brand new (refurbished) drive and everything looks kosher as near as I can tell.


So I'm at a loss.

I figure there HAS to be something amiss with the hardware since it takes so long for it to boot pass BIOS and on to the OS.  All I can think of is that there's something wrong with the motherboard, and that this something might also be interfering with it's ability to actually use a hard drive properly.  But how it could handle having Ubuntu installed to the hard drive just fine, but not bother to ever read from that drive is beyond me.

Thus I put it to those more learned than I.  Is this hardware?  Is it software?  Is it both?


System Stats, as best I know them:

512 MB RAM, 32 MB reserved for onboard video.
AMD Geode 1750 processor
I *think* it has a Biostar K7 motherboard.
Western Digital 20 GB hard drive

---

### Post by FleetAdmiral74 on 2007-06-21
WARNING:

GIANT WALL OF TEXT

um...please condense, lots more people will read and help!

---

### Post by atria on 2007-06-21
I think the hardware (more specifically the motherboard) broke down. Doubt it has anything to do with the OS itself.

Bad luck there!

---

### Post by Hobo Joe on 2007-06-21
Well, it definitely sounds like a hardware issue, I would suggest trying to install something else, Windows for example(I know, terrible... :() just to make sure it's not a software issue.




> **FleetAdmiral74 said:**
> WARNING:

GIANT WALL OF TEXT

um...please condense, lots more people will read and help!

This is not at all helpful, better to not post at all than post something like this. Besides, the more info the better, please refrain from posts like that.

---

### Post by Spektyr on 2007-06-21
I've got a stack of motherboards of indeterminate working-ness... it almost seems like it would be easier to try to install them to see if that solves the problem rather than trying to install XP.

Question: How well does Ubuntu handle hardware swapping (in general, and this type specifically)?

---

### Post by tgalati4 on 2007-06-21
Try cleaning the RAM with an eraser.  Reinsert.  Reseat all cards, cables, ribbons, etc.  Run memtest.  It's in the options menu on the Live CD.  Run at least 100 cycles (could take overnight).

This kind of troubleshooting is dreadfully slow, but we have to start somewhere.

Let us know when your memory checks out, then we can go to step 2.

---

### Post by the.phantom on 2007-06-21
i got lost in your post
but the boot order should be floppy,cd,then harddrive

in your bios setting does it recognize the drive that is in it ?
and if you replaced it
did you check the jumper settings on the drive?

if the computer is making noise
it sounds like a stalling fan ?? is the cpu fan turning at speed
and any cooling fans?

and you should be able to have the cover off  and find where the sound is coming from !

if a cpu fan it could be going into over temp 

but please re post in a easy to understand way


GO AFTER THE NOISE FIRST, after making sure your bios recognizes all 
and if you have a new video card...what are you doing with 32 meg shared memory?

---

### Post by Hobo Joe on 2007-06-21
> **Spektyr said:**
> I've got a stack of motherboards of indeterminate working-ness... it almost seems like it would be easier to try to install them to see if that solves the problem rather than trying to install XP.

Question: How well does Ubuntu handle hardware swapping (in general, and this type specifically)?

New motherboard = reformat, regardless of OS. Your getting a new BIOS when you switch motherboards, so everything has to be done again.

But Ubuntu does a pretty good job of switching graphics cards, RAM, and sound cards. Anything else is beyond my experience.

---

### Post by Spektyr on 2007-06-21
> **Hobo Joe said:**
> New motherboard = reformat, regardless of OS. Your getting a new BIOS when you switch motherboards, so everything has to be done again.

But Ubuntu does a pretty good job of switching graphics cards, RAM, and sound cards. Anything else is beyond my experience.

I've swapped motherboards and CPU's with XP before without a reformat.  It's thrown fits about it, but nothing really huge.  The most inconvenient part I've found is that you can end up with a lot of dead driver detritus clogging up registry and whatnot.  In fact, I could be wrong but I'm 99% certain I've taken hard drives straight out of computers as far back as Windows 98 and plugged them into completely different machines and had them boot up, provided I had the drivers for the new hardware handy.

I'll take your word for it that Ubuntu won't tolerate a motherboard swap, but I'm quite sure Windows can.  Not that I'm saying Windows is better, mind you.  The single, solitary reason I still run it at all is gaming.


And to whom it may concern: I have, do, and will continue to completely disregard any complaints that I string more than 1 sentence together per paragraph.  This is what differentiates sentences from paragraphs.  I do not abuse the run-on sentence, nor do I deploy the Paragraph-Of-Doom (where the entire post contains zero carriage returns).

If the fact that I don't stamp the Enter key after every few words is a problem, I would prefer you simply not read and not post than complain.

---

### Post by tgalati4 on 2007-06-22
If you change motherboards, then just run the Live CD.  That way you will get an operating system to work with and you can quickly see what works and what doesn't before committing to an install.

The hardware detection algorithm is robust, but swapping motherboards and expecting everything to work is unrealistic.  Linux expects perfect hardware; anything less and it will let you know.

---

### Post by Spektyr on 2007-06-22
Okay... I'm a retard.

Well maybe not, but I feel like one.

the.phantom had it right: jumpers.  That's what was causing the lethargic POST, the failure to boot, everything.  Now call me crazy, but when you put the jumper of your Master drive on the Master position everything ought to work just fine.  But I figured I'd humor him and pull the jumper off completely to prove that didn't work.

Except that it did work.  Thanks for all the help everyone... seems a tiny bit of metal wrapped in slightly more plastic was crippling my PC.

Well, I'm off to explore Ubuntu.

---

### Post by tgalati4 on 2007-06-22
In addition to what I said:  check the jumpers!

---

