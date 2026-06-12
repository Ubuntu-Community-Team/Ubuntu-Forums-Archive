---
title: "BIOS hard disk problem"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by owenb@theofficenet.com on 2007-08-02
]I have tried two different hard drives and the same problem manifests itself on both.
For example the factory value for the Maxtor Diamond 6L100P0 hard drive are:
IDE HDD Auto-Detection
IDE  Primary Master                 AUto
Access Mode                            CHS
Capacity                                   100GB
Cylinders                                   47993
Head                                          16
Precomp                                     0
Landing Zone                             47992
Sector                                        255

But Maxtor states that the values are (Logical Addressing Format)
Access Mode                            LBA
Capacity                                   100GB
Cylinders                                 12188
Head                                          255
Precomp                                     0
Landing Zone                             47992
Sector                                        63
The same sort of valuse were found on a Western Digital 80 Gig.  Why can't I get the factory values?

---

### Post by milosz.galazka on 2007-08-02
Hello,

But where is a problem? 
LBA addressing scheme is different then older CHS. [See that link]("http://www.boot-us.com/gloss11.htm")

---

### Post by Paulmd on 2007-08-02
> **milosz.galazka said:**
> Hello,

But where is a problem? 
LBA addressing scheme is different then older CHS. [See that link]("http://www.boot-us.com/gloss11.htm")

But what is a 100gb drive doing using CHS?  Almost all drives above 20gb use LBA, and a large portion of those above 10gb do too.

---

### Post by milosz.galazka on 2007-08-02
If CHS is  used only by bios and system is booting then everything is fine.

I tried to check my drive. System uses LBA but I couldn't get any informations from bios as it's notebook.

Quite interesting thread I hope that somebody will reveal this mystery.

---

