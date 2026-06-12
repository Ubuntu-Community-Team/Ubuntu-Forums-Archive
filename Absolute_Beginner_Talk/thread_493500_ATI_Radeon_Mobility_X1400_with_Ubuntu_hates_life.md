---
title: "ATI Radeon Mobility X1400 with Ubuntu hates life"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-05
I've looked as many places as I've can find, I've tried

> [http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell](http://ubuntuforums.org/showthread.php?t=399913&highlight=feisty+on+dell)
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)


I don't know what else to do, I've reconfigured xserver-xorg a bunch of times and tghe closest I can get is that it wont detect my screen when I use the ATI preferences. Please help this is driving me crazy.

---

### Post by oilchangeguy on 2007-07-05
while ubuntu is a very good os, it's not the only fish in the linux sea. check out other linux distros, to see if they'll work any better.

---

### Post by Korea91 on 2007-07-05
not sure about u but i got an answer to download the alternative u no in the downloading page thte thing u have to check yeah well thats wat im trying still downloading so dont no but best answer i can give u

---

### Post by snwbord2456 on 2007-07-05
I downloaded the alternative iso, thats how I installed unbuntu, but I can't get any farther than this.

---

### Post by snwbord2456 on 2007-07-05
If I need to use a different distros how do I pick one? I picked ubuntu to try because I've heard that its the easiest to learn on. I'm willing to devote time to understanding how the distros work what I'm most interested in honestly is the cube offered by beryl, sorry if thats not a purist enough, but I like eye candy.

---

### Post by oilchangeguy on 2007-07-05
> **snwbord2456 said:**
> If I need to use a different distros how do I pick one? I picked ubuntu to try because I've heard that its the easiest to learn on. I'm willing to devote time to understanding how the distros work what I'm most interested in honestly is the cube offered by beryl, sorry if thats not a purist enough, but I like eye candy.

start here:
[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions)

---

### Post by snwbord2456 on 2007-07-05
Is this the only choice though? Is it not possible to run Ubuntu on my system?

---

### Post by jackiecanev2 on 2007-07-05
I have a computer with the x1400, and with a little tinkering and tweaking, i've got it fully running with beryl and all. What problem are you having exactly?

heres a great guide on getting the ati non-proprietary driver working:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and another one on getting beryl running. beryl is a little trickier, since the x1400 doesnt run with aiglx, it has to be run with xgl, and there are some scripts to be created and configured. theres a step by step guide here

[http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html](http://ubuntu1501.blogspot.com/2007/01/beryl-with-xgl-on-ubuntu-610.html)

the guy who wrote it has a radeon express, but all the steps are identical and it works, i promise.

best of luck to you!

---

### Post by jackiecanev2 on 2007-07-05
ps: i found that 7.04 doesnt want to run the installer/live mode because of the video card; the easiest workaround ive found (and ive tried a lot, from installing it via terminal to reconfiguring etc) is to use the 6.10 installer, configure the card, and then update to 7.04

---

### Post by snwbord2456 on 2007-07-05
Awesome, thats what I think I'm going to do. Which .iso format did you use of 6.06 (the one that is liasted on Ubuntus website, I don't know where I'd find 6.1) to install on your comp?

---

### Post by jackiecanev2 on 2007-07-05
[http://releases.ubuntu.com/6.10/](http://releases.ubuntu.com/6.10/)

---

### Post by snwbord2456 on 2007-07-06
Awesome, everything except wifi is up and running now and after that is worked out I'll be installing beryl. Thanks for your help.

---

### Post by twiceasworn on 2007-07-06
Yay I am glad to hear you got it up and running.  I actually did the exact same thing on my computer running an x1300 card, worked like a charm.

---

### Post by CautionaryX on 2007-07-06
[http://releases.ubuntu.com/](http://releases.ubuntu.com/) has all the past releases of ubuntu available for download.

---

### Post by jairp on 2007-07-16
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

follow the above link: it worked wonders for me. i get 1680 x 1050 but desktop effects doesnt work!

---

### Post by jairp on 2007-07-18
Well, I have Ati X1400 in ubuntu fiesty. Initially, the screen looked horrible and the wide screen was not identified.  THen, i followed the post:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

and, Everything is working. the screen resolution is sweet: 1680X1050 and nthin more I ask. Although, getting Desktop Effects and Beryl working wud be awesome. But, I dont ask more than this.

---

