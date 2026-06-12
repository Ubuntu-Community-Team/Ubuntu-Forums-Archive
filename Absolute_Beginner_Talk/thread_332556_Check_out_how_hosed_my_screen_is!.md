---
title: "Check out how hosed my screen is!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by meng on 2007-01-06
Wouldn't you know it. I'd just set up my notebook computer with a decent Windows/Ubuntu dual-boot about a month ago, and last night the screen started doing this! (It's a Dell Inspiron 8200 if that's relevant.)

I figure that it's a problem with the monitor, not the graphics card, and if I tap the side of the monitor I can see a change in the pattern (although the display is still screwed). This problem may or may not be present during boot-up (including the initial BIOS and GRUB displays), but is definitely present after 1-2 minutes of use, and is also present in Windows, so it's obvious it is not an Ubuntu problem.

It is a little inconvenient to test it by connecting to another monitor, although I may do that if there is doubt as to where the problem lies.

So, can anyone confirm the nature of this problem? Is it the monitor that's hosed? And can you confirm that I'll have to get another computer? TIA

---

### Post by smoker on 2007-01-06
hi, meng,

i would definately try an external monitor,

haven't really a clue about this, but here are a couple of suggestions,

are you near any electo-magnetic fields, generators, large speakers, etc, maybe move away a bit and try,

if it is ok from a cold start, then maybe overheating could be a factor, are all the vents clear and is the fan/fans working?

if it has been dropped or jolted recently, maybe the connecter from the screen to the motherboard has loosened, though in a laptop it can be a pain to check,

you could maybe try reinstalling the drivers also,

best of luck

---

### Post by meng on 2007-01-06
Thanks smoker, E-M fields are not an issue, and it is not consistently okay from a cold start, although I can look into that further (the fans are working normally AFAICT). No recent drops, although the connector idea had crossed my mind. I really appreciate your suggestions, as I might as well do everything to try and nurse this computer back to health. I will report back!

---

### Post by Weyland on 2007-01-06
Hi Meng,

Its a good chance that the connecting lead between screen and mainboard has been jarred loose.

I had the same pattern with an old DELL CP laptop. 

Its a major pain to get at the connector though. My laptop required a fair amount of disassembly before being able to reach the target. A quick clean of the contacts and retightening the screws solved the problem.

Checkout DELL for downloadable service PDFs for your model.

Good luck!

---

### Post by meng on 2007-01-06
Weyland
Much appreciated. I'm encouraged to perhaps pay someone to do the disassembly/assembly, but I shall look into those downloadable manuals first. Great tip!
Meng

---

### Post by meng on 2007-01-06
> **smoker said:**
> i would definately try an external monitor
Well this turned out to be a great piece of advice. I was very surprised to find exactly the same problem with the external display, and it definitely wasn't a loose connection. Simultaneous notebook and external displays were identical, including flickering. Does this mean that the problem is with the graphics card itself and has nothing to do with the connector? Or am I missing something?

I can't imagine this is a driver issue (remember, Windows, Ubuntu and initial BIOS displays are all affected).

---

### Post by psycosmyth on 2007-01-06
I would suspect the card, is it the intel or other?
My screen on my Dell is doing some stuff as well, pixels of blue in color-rich areas.
My wife got mad cause I was on the box and not listening to her b*tch at me, she slamed the book shut. That's OK now she feels bad, maybe a new one is in the future;)

---

### Post by meng on 2007-01-06
It's an ATI Radeon Mobility 9000.

---

### Post by maddog39 on 2007-01-06
I think its the video card myself. When my ATI card went it did some stuff like that alot.

---

### Post by rbhigday on 2007-01-06
> **meng said:**
> Wouldn't you know it. I'd just set up my notebook computer with a decent Windows/Ubuntu dual-boot about a month ago, and last night the screen started doing this! (It's a Dell Inspiron 8200 if that's relevant.)

I figure that it's a problem with the monitor, not the graphics card, and if I tap the side of the monitor I can see a change in the pattern (although the display is still screwed). This problem may or may not be present during boot-up (including the initial BIOS and GRUB displays), but is definitely present after 1-2 minutes of use, and is also present in Windows, so it's obvious it is not an Ubuntu problem.

It is a little inconvenient to test it by connecting to another monitor, although I may do that if there is doubt as to where the problem lies.

So, can anyone confirm the nature of this problem? Is it the monitor that's hosed? And can you confirm that I'll have to get another computer? TIA


I dont think it your monitor, I get the same problem when I boot Ubuntu on my desktop which is also a dual boot with XP.  Only difference is my goes down about 1 inch and at the end has a line that connects all the collums. 

btw I have a ati x700 video card. the curse of the ati strikes again

---

### Post by smoker on 2007-01-06
i think it is your graphics chip then. you may want to take it to a local shop to confirm, or maybe check with dell support - is the warranty still valid?

you could try a post on the dell community forum and see if this is a common problem, there may be something you can do,
[http://www.dellcommunity.com/supportforums](http://www.dellcommunity.com/supportforums)

---

### Post by meng on 2007-01-06
Nah, this laptop is 4 years old, although it was a high-spec machine at the time and is still worth repairing. Looks like a replacement ATI card will be $150. Thanks everyone, more comments still welcome but it looks like I have a plan now.

---

### Post by stienman on 2007-01-06
I would first re-seat the video card and cables.  It's still possible that it's a connector problem.  In your laptop these are fairly easy to get to.  Make sure the laptop is off, all external cables are disconnected, and the battery is removed.  The plate between the keyboard and screen pops off with a little force, then there are screws at the top of the keyboard to unscrew.  Slide the keyboard forward, then lift up and lay it over the touchpad.  You should be able to move the keyboard out of the way without having to disconnect it.  You should be able to see the video card and the connector, if I remember correctly.  Gently wiggle the video connector to unseat it from the video card, then unscrew the video card, remove it, then put it back in place and re-attach the video cable.  Reassemble everything, and try it again.

If that doesn't resolve the problem, try booting an MS-DOS boot floppy or some other operating system (a simple live CD, or the start of a windows installation) to see if the problem continues.

If the problem is not detectable using these other OS's, then either your video driver is corrupted, or the video card is bad enough to affect some video modes and not others.  It may be that using a different video mode will resolve the problem.

A new/used video card can be purchased on E-Bay, or you can get it from Dell new.  The Dell part number printed on the video card is helpful if you don't want to fiddle with a different model/chipset/etc.  Could be a good time to upgrade the card as well.

Good luck!

-Adam

----------
Moving in southeast Michigan?  Buy my house: [http://ubasics.com/house/](http://ubasics.com/house/)
Interested in electronics?  Check out the projects at [http://ubasics.com](http://ubasics.com)
Building your own house?  Check out [http://ubasics.com/home/](http://ubasics.com/home/)

---

### Post by meng on 2007-01-06
Adam, much appreciated! (I'm fairly confident it's not a driver/software/OS problem though, since it persists in the BIOS splash as well as in my [dual-boot] Windows XP. Also it persists at different screen resolutions.) I will try the connector idea though.

---

### Post by chach man on 2007-01-06
I would try another card to confirm that it is the card. It could also be the motherboard and you dont want to go out and buy a $150 video card to find out it was a short on the motherboard someplace. 


(fyi if you ever want to check EMI (electro magnetic interference) just get an AM radio and you will be able to hear it :o )

---

### Post by gn2 on 2007-01-06
Does this behaviour occur when booted into Windows?

One of my laptops refused to run at a cool enough temperature, and has been returned to W2kPro, and now runs 10 degrees C cooler.....

---

### Post by Tenicus on 2007-01-06
> **meng said:**
> Wouldn't you know it. I'd just set up my notebook computer with a decent Windows/Ubuntu dual-boot about a month ago, and last night the screen started doing this! (It's a Dell Inspiron 8200 if that's relevant.)

I figure that it's a problem with the monitor, not the graphics card, and if I tap the side of the monitor I can see a change in the pattern (although the display is still screwed). This problem may or may not be present during boot-up (including the initial BIOS and GRUB displays), but is definitely present after 1-2 minutes of use, and is also present in Windows, so it's obvious it is not an Ubuntu problem.

It is a little inconvenient to test it by connecting to another monitor, although I may do that if there is doubt as to where the problem lies.

So, can anyone confirm the nature of this problem? Is it the monitor that's hosed? And can you confirm that I'll have to get another computer? TIA

Dont worry, thats just the matrix.

---

### Post by meng on 2007-01-06
> **gn2 said:**
> Does this behaviour occur when booted into Windows?
Sure does, and now even when starting cold.

---

### Post by EZEN on 2007-01-06
> **meng said:**
> Wouldn't you know it. I'd just set up my notebook computer with a decent Windows/Ubuntu dual-boot about a month ago, and last night the screen started doing this! (It's a Dell Inspiron 8200 if that's relevant.)

I figure that it's a problem with the monitor, not the graphics card, and if I tap the side of the monitor I can see a change in the pattern (although the display is still screwed). This problem may or may not be present during boot-up (including the initial BIOS and GRUB displays), but is definitely present after 1-2 minutes of use, and is also present in Windows, so it's obvious it is not an Ubuntu problem.

It is a little inconvenient to test it by connecting to another monitor, although I may do that if there is doubt as to where the problem lies.

So, can anyone confirm the nature of this problem? Is it the monitor that's hosed? And can you confirm that I'll have to get another computer? TIA

**Ummm...just a silly suggestion**. Sometimes things like this help out though.
Before dismantling your machine...
Maybe simply try running for a few hours with a LIVE cd installed. See if it happens.
I can personally attest to the fact that some laptops go funky with dual boot systems.
Mysterious things go on that look hardware related but aren't.

MAYBE it's one of those picky types of 'puters in which case it might like one OS or the other.
I dunno why but it does happen.
B)

---

### Post by gn2 on 2007-01-07
> **meng said:**
> Sure does, and now even when starting cold.

Have you tried disassembling and cleaning it?

---

### Post by meng on 2007-01-08
Thanks for all the responses! I took it into a shop for a "professional" opinion and was told that the VRAM was failing. So it looks like I'll need to replace it - fortunately I bought a system with a dedicated video card. It will be DIY since they're asking $375 for the PART alone, which I can get off ebay for <$150 (sure, buying off ebay is a risk but life is all about risks). And with the instructions on the Dell website, I should be able to do the replacement myself.

Wish me luck, I'm not out of the woods yet. But I am thanking my lucky stars that I bought a high-spec system way back then, because it's still worth salvaging even though it's 4 years old.

---

### Post by gn2 on 2007-01-08
> **meng said:**
> Thanks for all the responses! I took it into a shop for a "professional" opinion and was told that the VRAM was failing. So it looks like I'll need to replace it - fortunately I bought a system with a dedicated video card. It will be DIY since they're asking $375 for the PART alone, which I can get off ebay for <$150 (sure, buying off ebay is a risk but life is all about risks). And with the instructions on the Dell website, I should be able to do the replacement myself.

Wish me luck, I'm not out of the woods yet. But I am thanking my lucky stars that I bought a high-spec system way back then, because it's still worth salvaging even though it's 4 years old.

Before you spend any cash open the laptop right up and give the insides a thorough clean, paying particular attention to cooling ducts/fans and the GPU.

Could be the VRAM's failing because it's getting too hot due to restricted airflow.

Won't hurt to try first?

---

### Post by meng on 2007-01-08
> **gn2 said:**
> Won't hurt to try first?
True, I've opened it up and everything looks surprisingly clean! About to give it a test though.

---

### Post by meng on 2007-01-09
No dice :( Still giving screen errors even after checking/cleaning connectors, with fans working and keyboard open, and despite a cold start. Ventilation failure seems less likely. Now waiting for a replacement video card to arrive by post. It's a reasonable "gamble" in my opinion, if that doesn't work I guess I'll be looking for a new computer. Thanks for all the help.

---

### Post by meng on 2007-01-10
Update (in case anyone cares anymore!): received replacement video card, installed, seems to be working fine so far. Computer has been on for 30 minutes continuously, no video problems noted. Fingers crossed, but if it remains good for another 30 minutes I should be home-free. (I kept trying the old card until the bitter end, it just continued to get worse...) Once again, thanks to everyone who offered advice, and for those who stayed tuned until now, I hope you enjoyed the happy ending (almost-ending).

---

