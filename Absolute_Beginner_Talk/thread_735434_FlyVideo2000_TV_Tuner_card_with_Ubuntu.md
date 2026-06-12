---
title: "FlyVideo2000 TV Tuner card with Ubuntu"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by howejustin on 2008-03-25
Hey all,

I have an old FlyVideo2000 TV Tuner card that works in Windows just fine, however I remember that when I tried to install it with Mandriva or Gentoo some years ago it would not go. Do any of you know about this specific card's compatibility with 7.1 Ubuntu Gutsy? 

If nothing else, I'm installing Xen today and can just switch over to Vista when I need to use iTunes' video capability to sync with my iPod and watch ABC.com's episodes :lolflag: So I can also use it for TV.

---

### Post by mwcrowley on 2008-03-25
[www.google.com/linux](www.google.com/linux) is your friend
Try installing tvtime to see if the card works with that.  Support on old capture cards can be dodgy.  It looks like this card is supported by the bttv driver but you won't know for sure until you put it in the box and try it out.

[http://www.bttv-gallery.de/](http://www.bttv-gallery.de/)




Lifeview Flyvideo Series:
-------------------------
  The naming of these series differs in time and space.

  Identifying:
  1) Some models can be identified by PCI subsystem ID:
      1852:1852 = Flyvideo 98 FM
      1851:1850 = Flyvideo 98
      1851:1851 = Flyvideo 98 EZ (capture only)
  2) There is a print on the PCB:
      LR25       = Flyvideo (Zoran ZR36120, SAA7110A)
      LR26 Rev.N = Flyvideo II (Bt848)
           Rev.O = Flyvideo II (Bt878)
      LR37 Rev.C = Flyvideo EZ (Capture only, ZR36120 + SAA7110)
      LR38 Rev.A1= Flyvideo II EZ (Bt848 capture only)
      LR50 Rev.Q = Flyvideo 98 (w/eeprom and PCI subsystem ID)
           Rev.W = Flyvideo 98 (no eeprom)
      LR51 Rev.E = Flyvideo 98 EZ (capture only)
      LR90       = Flyvideo 2000 (Bt878)
		   Flyvideo 2000S (Bt878) w/Stereo TV (Package incl. LR91 daughterboard)
      LR91       = Stereo daughter card for LR90
      LR97       = Flyvideo DVBS
      LR99 Rev.E = Low profile card for OEM integration (only internal audio!) bt878
      LR136	 = Flyvideo 2100/3100 (Low profile, SAA7130/SAA7134)
      LR137      = Flyvideo DV2000/DV3000 (SAA7130/SAA7134 + IEEE1394)
      LR138 Rev.C= Flyvideo 2000 (SAA7130)
	        or Flyvideo 3000 (SAA7134) w/Stereo TV
		   These exist in variations w/FM and w/Remote sometimes denoted
		   by suffixes "FM" and "R".

      Lifeview.com.tw states (Feb. 2002):
      "The FlyVideo2000 and FlyVideo2000s product name have renamed to FlyVideo98."
      Their Bt8x8 cards are listed as discontinued.
      Flyvideo 2000S was probably sold as Flyvideo 3000 in some contries(Europe?).
      The new Flyvideo 2000/3000 are SAA7130/SAA7134 based. 

  "Flyvideo II" had been the name for the 848 cards, nowadays (in Germany)
  this name is re-used for LR50 Rev.W.
  The Lifeview website mentioned Flyvideo III at some time, but such a card
  has not yet been seen (perhaps it was the german name for LR90 [stereo]).
  These cards are sold by many OEMs too.

  FlyVideo A2 (Elta 8680)= LR90 Rev.F (w/Remote, w/o FM, stereo TV by tda9821) {Germany}
  Lifeview 3000 (Elta 8681) as sold by Plus(April 2002), Germany = LR138 w/ saa7134

---

