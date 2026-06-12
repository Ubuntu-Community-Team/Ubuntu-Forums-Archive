---
title: "Installing Linux on old Mac"
date: 2009-09-01
forum: Apple Hardware Users
---

### Post by tazz4vr on 2009-09-01
Okay, no clue where to start.  So here goes.  I received 2 computers, one is an old Mac- 98 and it actually works, sort of.  I was unable to get past the log in screen, so followed some info per a friend, and now can not get the thing past the boot-text stuff.  Something to do with the 'firmware' thing he said.  

There are no installation discs available.  I would like to use this Mac as my linux training computer.  So my questions would have to be: 
1.  if there are no discs to even get in the computer, is it a lost cause?  
2.  if it isn't a lost cause, can linux be installed over what is currently in it?
3.  what version would be best for me, as I have no knowledge on what I am doing, but I would like to at least try.
4.  there are lot of sites offering help, but at this point it is all Greek to me even the apple sites, aside from Ubuntu, are there any other sites that can be recommended?  I would just assume stay with Ubuntu, but not sure if this is something I should be doing in an apple site... doe's this make sense?

---

### Post by tazz4vr on 2009-09-01
Okay, still doing some poking around.  Went into a linux site and it suggested Jaunty Jackelope... well not really, that is basically what I was advised they were sending me...upon reviewing the Ubuntu desktop edition version.  Excited and yet nervous, have to wait a few weeks though, dang it!

---

### Post by schauerlich on 2009-09-01
If your Mac uses PowerPC chips, then you have to get a distro which is specifically made for PowerPC. You can find some helpful links here:

[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

---

### Post by tazz4vr on 2009-09-01
let me see if I can figure out how to find out if this puter has PowerPC Chips, i'll get back to you on that one...but I think it is, per wiki- PowerPC 750.  Unable to get past the login screen to verify on computer.  But will definitely check out the link you provided, thank you.

---

### Post by schauerlich on 2009-09-02
If it's an iMac, it's PowerPC.

---

### Post by tazz4vr on 2009-09-02
Cool... I have been going over some of the links you provided, why can't apple be as informative and semi-easy to understand?  Or is it just me?  Even calling the store near me, I heard, 'um, hmmmm, can you hold please?', ughhhhhhhhhhhhhhhh! ](*,) I use to have patience, really I did, but in less than 2 days time, I lost it somewhere.  But not to fear, I have a Bear that I kick for such moments...and then all is good again for a little while.

---

### Post by tazz4vr on 2009-09-02
Wow... I am so whiny tonight... putting myself on a time-out!

---

### Post by 3rdalbum on 2009-09-02
PowerPC 750 is indeed a PowerPC chip; a G3 if I remember correctly.

If it's a beige Macintosh, then you need to have the classic Mac OS installed and available in order to boot Linux. If the case of the computer is not beige, then you can boot the CD directly by holding down the C key; this is assuming that you've got a version of Ubuntu that is compiled for PowerPC rather than for Intel/AMD processors.

The final problem is that Macintoshes of that era only shipped with 32 megabytes of RAM, and 256 megs (the minimum for Ubuntu today) was an awesomely massive amount... in fact some of the Macs from that era simply couldn't access that much RAM. It could be an expensive exercise to track down the SDRAM that your Mac uses, in order to upgrade it to 256 megs.

Good luck.

---

### Post by tazz4vr on 2009-09-02
The Mac is orange in color, at least comparing it to a tootsie-pop, and yes, I have kids, we have tootsie-pops, it was a side by side comparison, it's orange, but all others say tangerine.

In regards to the version compiled for PowerPC vs Intel/AMD, when I requested the cd and the response was that Jaunty Jackalope was being sent, I never received an option for one or the other (Power/Intel), and this was done via the Ubuntu Site.  So, I again attempted to request a cd thinking I had missed something, but the same thing.  

I tried to find online, via Ubuntu and google info on getting such a disc, but I think I am stuck on stupid because I can not find anything that says specifically for PowerPc or specifically for Intel/AMD processors, or is the disc I am getting a general all around you can install on your mac disc?  Or my brain is on hold this morning.... it's been a long night of reading, re-reading, etc....

---

### Post by tazz4vr on 2009-09-02
Just received a response from another site, I am being told that Jaunty Jackalope may not be compatible with PPC :shock: ](*,), where's my Bear!...instead I would need a distro called Cosmic Koala, wait,no, Karmic Koala... something like that, but, that is not out until October :rolleyes:, figures!

---

### Post by tazz4vr on 2009-09-03
Ubuntu 8.04.3 desktop, is this the same thing as Hardy Heron or are these two totally different versions?

---

### Post by snowpine on 2009-09-03
> **tazz4vr said:**
> Ubuntu 8.04.3 desktop, is this the same thing as Hardy Heron or are these two totally different versions?

Ubuntu 8.04.3 = Hardy Heron

You never answered the question about how much ram is in the computer; if you don't have 256mb or more, you are wasting your time...

---

### Post by tazz4vr on 2009-09-03
Per AppleHistory, the specs are as follows... from this, which amount of Ram is for this computer? I am confused on this one as there are several instances in reference to 'Ram'.  Also, if the prior owner upgraded/added to it, I am not able to get past the login screen to find it or how much more was added, or is this something that, against my better judgement, can i take it apart and see a chip or something?  
Let me put it this way, I took apart my travel coffee mug to clean all the little nooks and crannies, my son had to put it back together! Me and tools don't mix, several people can attest to that!

CPU: PowerPC 750 "G3"
CPU Speed: 233 MHz
FPU: integrated
Bus Speed: 66 MHz
Data Path Width: 64 bit
Address Width: 32 bit
ROM: 1 MB ROM + 3 MB toolbox ROM loaded into RAM
RAM Type: 144 pin SO-DIMM
Minimum RAM Speed: 100 MHz
Onboard RAM: 0 MB
RAM slots: 2
Maximum RAM: 256 MB
Level 1 Cache: 32 kB data, 32 kB instruction
Level 2 Cache: 512 kB backside, 1:2
Expansion Slots: mezzanine

---

### Post by snowpine on 2009-09-03
According to those specs, you have 0mb of onboard ram. If that is true, it explains why the computer won't boot. :) I will let a Mac expert weigh in on a more accurate way to tell how much you have...

---

### Post by tazz4vr on 2009-09-03
When we attempted to get past admin, I had to hold 'apple + S', it got me to the text input screen, but nothing ever took.  It kept repeating with 'unknown word' at end of the command lines.

If I get back into it for a repeat of everything, will this information help figure out what is up with the puter?

---

### Post by tazz4vr on 2009-09-03
My little bundle of headache.... meet Tess

[IMG]http://ubuntu-utah.ubuntuforums.org/picture.php?albumid=425&pictureid=4693[/IMG]

---

### Post by jml on 2009-09-04
The picture was most helpful.  This looks like a first or second generation iMac.  Here is a Wikipedia reference.

[http://en.wikipedia.org/wiki/IMac_G3](http://en.wikipedia.org/wiki/IMac_G3)

It was not really designed to be easily user upgraded so I think that you are most likely have standard hardware which includes 32 meg of ram and a 4 gig hard drive.  With that type of hardware Ubuntu will not run.  You might be able to do a base install if Debian 5.0 for the power pc architecture.  See web site below.

[http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/)

If successful you will have a computer that will run with a command line interface, but not a graphical user interface.

Good luck.

Joe

---

### Post by tazz4vr on 2009-09-04
Thank you for the info, will review the link for Debian.  However it appears that I will have to actually consider purchasing something compatible so that I can learn linux the way I want to, not by way that is available.

---

### Post by oswaldkelso on 2009-09-11
That's an early imac you'll need at least 256mb of ram to run a graphical  setup. Even then a full desktop will be slow. It will be slow anyway!! Your choices for PPC 

[http://www.ppclinux.info/wiki/maclin](http://www.ppclinux.info/wiki/maclin)

For an _easy lite install_ debian xfce/lxde CD is the way to go. I used to do the blackbox install in my sig but it's way more work. If you go that route read it for the tips :)

---

### Post by tazz4vr on 2009-10-08
This whole issue with my little bundle of headache is on hold..... I ordered/sent for new computer, she'll be here on Mon or Tuesday.... so excited... yeahhhhhhhhhhhhh!

---

