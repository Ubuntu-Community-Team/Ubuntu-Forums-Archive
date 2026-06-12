---
title: "Belkin Wireless PCMCIA Card in Thinkpad"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by serafin630 on 2008-03-21
I had such a good experience "reviving" an old Dell desktop with Xubuntu so I tried a LiveCD on an old IBM ThinkPad.  Everything worked fine except for the Belkin Pre-N wireless PCMCIA card, which isn't recognized.

I also tried OpenSUSE and Slacker (sic) with the same results (i.e. no wireless connectivity and no apparent recognition of the card).

Do I need to do something to get wireless internet access on this laptop?  Help would be appreciated, and remember that I am in the ABSOLUTE BEGINNER area.....

---

### Post by spiderbatdad on 2008-03-21
Run iwconfig with the card in and post the results, please.

---

### Post by kwacka on 2008-03-21
removed

---

### Post by aLsanomo on 2008-03-22
What version of Ubuntu are you running?

---

### Post by serafin630 on 2008-03-23
> **spiderbatdad said:**
> Run iwconfig with the card in and post the results, please.


I've hit another wall in this project of mine that might actually be the subject of another thread.  I now can't seem to get XUMBUTU to load  and run from the LiveCD on this T20 at all.  

If I run it with default video settings. it gets to a certain point and then stops, leaving a completely blank black screen and nothing more.

If I adjust the video settings down I get a desktop with icons but no bars (and their drop down menus) at the top or the bottom of the screen.

---

### Post by spiderbatdad on 2008-03-23
> **serafin630 said:**
> I've hit another wall in this project of mine that might actually be the subject of another thread.  I now can't seem to get XUMBUTU to load  and run from the LiveCD on this T20 at all.  

If I run it with default video settings. it gets to a certain point and then stops, leaving a completely blank black screen and nothing more.

If I adjust the video settings down I get a desktop with icons but no bars (and their drop down menus) at the top or the bottom of the screen.

Didn't realize you were trying to run xubuntu; should have known.
At the options screen after starting up with the live cd, hit F6 and delete the end of the kernel line "ro --quiet splash." Type in "noapic nolapic" without quotes.

---

### Post by serafin630 on 2008-03-25
No change except that it took a lot longer (and a lot more CD reads) to start up.  I still ended up with a desktop with icons but no top or bottom bar.

One thing that was different though was that I didn't have your exact line to delete when I pressed F6.  I ended up only deleting quiet.splash because the other text was not present.

---

