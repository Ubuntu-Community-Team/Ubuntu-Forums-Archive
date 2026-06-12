---
title: "extra newbie... a bunch of questions"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by wcampbell115 on 2006-03-20
Ok, so I am brand new to the linux game, been stuck in Microsoft land since my apple IIe went out of style.  I really like ubuntu though and even got it running most of the time.  The machine I am running looks like this:

------------
Memory - 383Mb

Motherboard
	Intel Dual Pentium II Motherboard w/ Integrated SCSI [Part #4000294] 	
Processors
	Dual Intel 300 MHz Pentium II Processors [Part #CPUSAC013AAWW] 	Support 
Sound Cards
	Audio PCI Wavetable Sound Card [Part #6000708] 	Support Docs

*The gateway serial number says I should have this:
Video Cards
	AccelGraphics Permedia II AGP 8MB SGRAM Video Card Revision 1 
* but I think I saw 'Rage Pro Turbo' or something like that when i had the case open

Sound Card PnP Audio Cable, Rev 2 [Part #SNDCBL003ABWW] 	
----

The bios is from like 1998 or something so acpi seems to make things blow up... i found linux because (luckily) no MS OS since win 98 would install.  The scsi adapter  isnt doing anything because the drive is too loud for my girlfriend.  I removed it.

So now on to the help I need....

1.  for some reason whenever I go to a site with embedded windows media, the whole machine freezes up and I have to reboot the machine (power button).

2. last time I did this, I ran installed the reccommended updates, and there was some kind of kernel problem and the machine wouldnt boot untill I wiped the whole thing... ok yeah, dont do that again... right.. any ideas on that?

3.  Most of the hardware in the device manager says 'unknown'... where do i start?

....

any advice is worth giving... 

Thanks,

W.

---

### Post by cilynx on 2006-03-20
One of the better places to start on hardware ID is 'lspci'.  It tells you everything you have on the PCI bus.  The terms it gives you are good for throwing at Google to find out which drivers you need loaded.

As for embedded Windows Media, is this with or without mozilla-mplayer installed?

Kernel updates are always fun.  You usually don't actually have to do the wipe, but it takes about 5 years of experience to figure that out.

---

### Post by wcampbell115 on 2006-03-20
I have two ide drives... whats the best configuration for that?  swap partition on seprate drive?

---

### Post by wcampbell115 on 2006-03-20
thanks so much for your help... should keep me busy for a few hours...mozilla-mplayer eh? that sounds like something I want.... i think it was without

---

### Post by takayuki on 2006-03-20
welcome. 

i'm assuming you're using firefox, correct?  what site with windows media froze your box?

i get the same "unkown device," "unknown vendor"'s in the device manager and everything runs great.

keep digging.  there's a bunch of helpful and knowledgeable (unlike myself!) people here!

takayuki

---

### Post by cilynx on 2006-03-20
For a two drive setup, I generally put /home and swap on one drive and everything else on the other...assuming the drives are the same anyways.  If you're more interested in fun stuff than capacity, you could play with software RAID or some such as well.

---

