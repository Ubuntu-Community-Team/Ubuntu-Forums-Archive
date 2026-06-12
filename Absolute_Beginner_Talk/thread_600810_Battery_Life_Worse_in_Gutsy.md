---
title: "Battery Life Worse in Gutsy?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-11-02
I recently upgraded from Feisty to Gutsy and immediately noticed a drop-off in battery life.  I have disabled indexing, and am running on a brand spanking used Dell Inspiron | 8000 700mhz pimped hardcore with 512mb RAM.  So, as you can imagine, I am not running any desktop effects, etc.  Back to the story at hand.  On feisty, I could expect 6-8 hours of battery life (running two batteries) under a normal work day.  That number is now down to 2-3 hours of battery life.  I have not changed usage behavior significantly, if at all.  Can anyone think of anything I might be missing?  I have tried changing the gconf-editor with no real changes in behavior.  I am actually running at a lesser resolution now than I was under feisty.  Baffled=me.  I thought battery life was supposed to improve with this release, is it really all that bloated?

---

### Post by bmk789 on 2007-11-02
I noticed a slight decrease in calculated battery time after upgrading to Gutsy, but the power applet showed two different calculated times.  Are you posting based on calculated times or actual run-to-dead experience?

---

### Post by Max Luebbe on 2007-11-02
There was something on slashdot about this a while ago.
The 2.6.22 kernel does have some cool powersaving features, such as tickless idle - but if I recall, 7.10 does have worse mobile performance due to the running more services that require more cpu usage than 7.04 did.

I can't find the article, but there's one out there where battery life on every release of Ubuntu is compared.

You also might want to look into Intel's PowerTop

---

### Post by soaklord on 2007-11-02
Both perceived and listed appear to be shorter.  7.04 used to show some ridiculous times like 12 hours of life, but I knew I could get 6.  Even leaving the machine idle, I don't get more than 3 now.

---

### Post by dealmaker on 2007-11-12
me too.  I am using dell inspirin 1500.  When I was using 7.04, my laptop lasts about 5 hours.  After upgrading to 7.10, it lasts only 3 hours and then it just shut off itself.  No change in configuration.  Someone please fix it.

---

### Post by rundee_f on 2007-11-18
*bump

i happened to me either... someone please... :(

---

### Post by Technoviking on 2007-11-18
I have had better battery life under Gutsy than Fiesty. I would suggest looking at powertop, also running things compiz-fusion, which is on by default, can suck the battery faster.

```
sudo apt-get install powertop
sudo powertop
```

---

### Post by wil313 on 2007-11-18
Go to synaptic manager and tell it to install ubuntu-laptop-mode...

---

### Post by rundee_f on 2007-11-19
then what happen?? I just installed Gutsy 3 hrs ago and now it's still updating so i cant do another synaptic running... My battery life reduces by half! It drives me dizzy..

---

### Post by russo.mic on 2007-11-19
I have noticed a drop off in the battery life on my MBP, pretty serious actually.  I've found that using laptop_mode is a big help.  

just man laptop_mode from the terminal for info.  

Russo

---

### Post by rundee_f on 2007-11-19
what is the different between laptop-mode-tools and ubuntu-laptop-mode? coz i olredi had ubuntu-laptop-mode and when i mark laptop-mode-tools, SYnaptic told me to remove ubuntu-laptop-mode..

i guess they have the same function, dont they?

---

### Post by rundee_f on 2007-11-21
*bump*

anyone can help me with this battery life issue?? i alredy installed  **laptop-mode-tools**...
this thing frustates me... :(

---

