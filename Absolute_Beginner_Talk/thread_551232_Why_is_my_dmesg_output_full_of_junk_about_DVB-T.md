---
title: "Why is my dmesg output full of junk about DVB-T"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by jc508 on 2007-09-14
Hi,
My dmesg just returns 1900 lines like the following. How do I get to tell me the useful things ?

fault dtv settings: xc3028_DTV8_2633.i2c.fw
[  524.848185] xc3028-tuner.c: sending extra call for DVB-T
[  524.848191] Loading 7MHz Bandwidth settings: xc3028_DTV7_2633.i2c.fw
[  525.783616] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw
[  525.812242] xc3028-tuner.c: sending extra call for DVB-T
[  525.812249] Loading 7MHz Bandwidth settings: xc3028_DTV7_2633.i2c.fw
[  526.135378] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[  527.094815] Loading base firmware: xc3028_8MHz_init0.i2c.fw
[  527.363216] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw
[  527.391716] xc3028-tuner.c: sending extra call for DVB-T
[  527.391723] Loading 7MHz Bandwidth settings: xc3028_DTV7_2633.i2c.fw
[  528.323021] Loading default dtv settings: xc3028_DTV8_2633.i2c.fw

Thanks for any help

JC

---

### Post by aJayRoo on 2007-09-18
Well it does help if you know what you are looking for, that way you can pipe the output of dmesg into grep and search for a particular thing. For example, when I installed my DVB tuner I actually wanted to see the parts of dmesg output that referred to DVB so I used the command:
```
dmesg | grep DVB
```
which printed out all lines containing 'DVB'. The grep command can take a regular expression as a parameter (in my example it was simply the string 'DVB') and so can be an extremely powerful and flexible tool for finding exactly what you want. Unfortunately I am no expert on regular expressions so I can't help you much with those but the command format above combined with the right regular expression can almost certainly deliver what you require. I would recommend reading up on regular expressions as they are an extremely useful tool. Hope that helps.

---

### Post by persev on 2007-09-18
[QUOTE=aJayRoo;
```
dmesg | grep DVB
```
[/QUOTE]

Okay here is a silly question, how do you make that symbol between dmesg and grep? Aside from copy and paste?

---

### Post by aJayRoo on 2007-09-18
Well on a UK keyboard it is shift and backwards slash. Usually it will be on a key requiring shift. Confusingly it often appears as two shorter vertical lines on top of each other like '--' but rotated 90 degrees! Good luck tracking it down :)

---

### Post by persev on 2007-09-20
> **aJayRoo said:**
> Well on a UK keyboard it is shift and backwards slash. Usually it will be on a key requiring shift. Confusingly it often appears as two shorter vertical lines on top of each other like '--' but rotated 90 degrees! Good luck tracking it down :)

AHHH... there it is! Another one of life's mysteries solved!

---

### Post by jc508 on 2007-09-21
Thanks aj-Roo
but you miss my point - that is ALL there is in the dmesg file the whole thing is full of that and only that.
I am trying to search for other things but they just arn't there
JC

---

### Post by jc508 on 2007-11-17
Solved.
The messages were coming from module xc3028-fe due to over zealous diagnostic messages.  I think the authors expected the modules to be called once but at startup it is called hundreds and hundreds of times.
I hacked at xe3028-fc.c to only issue failure messages. Rebuilt - and now the log has some room for all the other messages I was looking for.

---

