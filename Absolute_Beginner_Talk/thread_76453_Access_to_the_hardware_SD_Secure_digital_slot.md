---
title: "Access to the hardware SD Secure digital slot"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by bengtfalke on 2005-10-15
Now almost all of my hardware works the way i want it to.......:) 

The last issue is to get permanent access to the **Secure Digital (SD)** slot on my portable computer Fujitsu-Siemens P7010....

I am looking for a solution that works the same way as inserting a CD so the filesystem on the card automaticly gets mounted and gets visible on the desktop.

The same way as a DVD or CD gets mounted.

Does anybody have any ideas?

regards/falke

---

### Post by towsonu2003 on 2005-11-24
I read in too many places (including the linux laptop sellers who sell such laptops but tell you that) that those slots don't work (no drivers I believe)... maybe linux geeks don't like them? j/k

---

### Post by bengtfalke on 2005-11-24
I have read somewhere that you often can mount them manually... as far as I know that should implicate that it is possible to write a program that does this automatic. Has anybody done that yet or do I have to refresh my 20 years old C-skills.....   ;o)
regards/falke

---

### Post by sinaen on 2006-05-06
I have also been in great search for the memmory card reader. but havent found anything about it. well i have found some stuff. but that's not sure its the right stuff. 

heres what i have found. unfortunately i havent tested it yet because i have managed a way to use my memory cards in the gadgets they come in?

[http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd)

please tell me if you get it to work. i am cutting down on my computer time. have too many other projects i want to do

---

### Post by sinaen on 2006-05-22
[QUOTE=sinaen]I have also been in great search for the memmory card reader. but havent found anything about it. well i have found some stuff. but that's not sure its the right stuff. 

heres what i have found. unfortunately i havent tested it yet because i have managed a way to use my memory cards in the gadgets they come in?

[http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd)

please tell me if you get it to work. i am cutting down on my computer time. have too many other projects i want to do[/QUOTE]

This project doesnt seem to be the correct for the reader in my  laptop p7010 :/ and i cannot find where to download the patch, you ought to think it should be somewhere on the intro-page :( 
and definitely the reader in my (our) laptop does support sd pro as well and it isnt mentioned at all.

Anybody got some clue or whatever on this card reader yet? maybe dapper have something?

---

### Post by bigken on 2006-05-22
In my exprience they wont work in 5.10 but in dapper no probs tried for months in breazy no joy in dapper out the box :D

---

### Post by sinaen on 2006-08-14
> **bigken said:**
> In my exprience they wont work in 5.10 but in dapper no probs tried for months in breazy no joy in dapper out the box :D

do you mean it wont work in dapper? Or that it will work? 
Anyhow it doesnt, cause ive run dapper for months now and no support for no memmory-card-reader :(

---

### Post by sinaen on 2007-03-18
i found that the kernel supports TI/ricoh memmory card readers but the default kernel in ubuntu linux is not implementing those drivers even as modules :( the only way is to compile your own kernel with those modules and then voila!

---

