---
title: "Setting IE emulation for wine....I'm stuck..."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-07-01
Hi,
I'm following the instructions given on [www.winehq.org](www.winehq.org) to set up the needed emulations to have it seem like wine has Internet Explorer installed. (Apparently you can't directly install IE on wine; it will break it if you do).

So first, I ran this:
```
wine iexplore
```
And from what I could tell, that automatically downloaded and installed Gecko which is necessary for that part. 

Then I ran this:
```
regedit
```
and I've tried to install these keys:
```
6.0.2800.1106 and 62800.1106
```
but I don't know where I'm going there or where exactly to put them. 

I'm doing something wrong here but what is it?

BTW, the reason for all this is: Dreamweaver MX is stuck with me on CrossOver in a bad way (fatal exception). So I want to try DW MX with wine. But MDAC needs to be installed for DW MX to run and MDAC must have IE4sp2 or higher installed. Hence my need to have IE on wine.

I appreciate any help or assistance. 

Many Thanks, Frank B.

---

### Post by Malibu Illusion on 2007-07-01
I suggest taking a look at the [IEs4Linux](http://www.tatanka.com.br/ies4linux/page/Main_Page) project.

---

### Post by Brightbelt on 2007-07-01
Thanks Malibu. I totally forgot about that project. I actually downloaded it for another computer a while back but haven't thought about it since. Many Thanks for your help.

...Frank B.

---

### Post by Brightbelt on 2007-07-01
Well, I installed Both IE 5 and IE 6. For some reason, the file MDAC_TYP.EXE does NOT recognize that IE explorer has been installed at all.

I have two (2) IE icons in wine glasses on my desktop. What more can I do here?

Thanks, Frank B.

---

