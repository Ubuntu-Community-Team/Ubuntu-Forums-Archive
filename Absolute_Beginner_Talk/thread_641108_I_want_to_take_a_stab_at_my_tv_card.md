---
title: "I want to take a stab at my tv card"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-12-15
I just removed my video card I virtually have never used (ati radeon x1300 if anyone wants it send me a message) and now have an empty PCI slot.

Well I was digging around through a box of stuff I had from a couple years ago and found a tv card I never really got to work on Windows.  It's an xpert tv-pvr pci series from v-stream [http://www.kworld.com.tw](http://www.kworld.com.tw)

The problem here is that I have really never just taken something like this that has virtually no support anywhere and made it work.

The output of lspci for the card is:

```

02:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

I really have no idea where to go from here to make this functional.  Any help or ideas is appreciated.

---

### Post by rsambuca on 2007-12-15
Looks like you may be in luck.  Have you [looked here]("http://www.linuxtv.org/v4lwiki/index.php/Bttv_devices_%28bt848%2C_bt878%29")?

---

### Post by siciliancasanova on 2007-12-15
Ha, awesome.  Thank you.

---

### Post by Methuselah on 2007-12-15
I have a card with that chipset.
XSane tries scan from it but tv programs don't seem to recognize it.
Good luck with yours.

---

### Post by siciliancasanova on 2007-12-15
Yeah and mine isn't listed on that page but an almost identical one is so I'm going to mess around with this tonight modifying /etc/modules.conf

I've got a 50in lcd 15 feet away from me, so don't ask me why I need this on my computer.  Guess I just enjoy messing around with stuff.

---

