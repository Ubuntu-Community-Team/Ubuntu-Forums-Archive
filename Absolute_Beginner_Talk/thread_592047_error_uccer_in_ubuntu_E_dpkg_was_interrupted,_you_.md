---
title: "error uccer in ubuntu E: dpkg was interrupted, you must manually run 'dpkg --configu"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by banga on 2007-10-26
I AM NEW IN UBUNTU
WHEN I RY TO INSTALL ANYTHING THEN AN ERROR IS OCCUR
WHICH IS...
>>>>>>>>>
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
>>>>>>>>>>>
PLZ HELP ME TO AVOID THESE PROB
THANKS IN ADVANCED

---

### Post by taurus on 2007-10-26
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Turn the cap off!

---

### Post by swoll1980 on 2007-10-26
open a terminal under applications-accessories then type sudo dpkg  --configure -a
 hit enterThen enter your pswrd you wont see your pswrd while your typing it then hit enter again sit and answer any questions it ask you this can take some time

---

### Post by banga on 2007-10-26
thanks friend
it is workin
nd solved my problem
thanks again

---

### Post by 97lastr on 2007-11-25
Hi,

I'd like to thank you helpers also...

I've just started using linux and although somewhat a technical person I was so glad that there was someone there to give an easy answer!!

Cheers,

97lastr. :guitar:

---

### Post by ScrewdriverClock on 2008-02-09
Hahha, sorry for the bump but this was extremely helpful, i was having this problem today. Thanks everyone for knowing this stuff :P

---

