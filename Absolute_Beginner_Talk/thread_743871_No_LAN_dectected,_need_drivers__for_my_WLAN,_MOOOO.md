---
title: "No LAN dectected, need drivers  for my WLAN, MOOOOOO!!!"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by ConorBuzz on 2008-04-03
Hello 
So I installed Ubuntu 6.06 LTS , and my wireless network card won't work as i have to use ndiswrapper. to get ndiswrapper I have to install if from the net ? but I can connect to my router as my onboard dell etherent card isn't detected, just "lo"

Is there any bundles that I can download that have all the "Network manager, ndiswrapper, bcm43xx-fwcutter, drivers for my graphics  card? 

I'm thinking of going back to SUSE , it's  a bit harder but nearly everything is on the  DVD. 

I wanted to completely switch to Linux and banish Windows to the wastes, can some one please  help me do this ? 

So, how do I install and run the software that allows  me to connect to the internet , when I can't connect to the  internet ? :/

Thank you all for your help, and I think that is  forum rock, I had so much trouble installing Ubuntu , but you guys  & gals helped  me out 

Conor

---

### Post by Xiong Chiamiov on 2008-04-03
Anything available in the official repositories is also at packages.ubuntu.com.  You can [search for things]("http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=gutsy&section=all") there and then install them using GDebi.

---

### Post by ConorBuzz on 2008-04-03
Thank you, I'm in the process of writing a blog at home , a 'beginners guide written by a beginner"

I think that when you are used to linux that you assume so much stuff. 

or maybe I'm just a twit. :) 

So, I can install the  packages, cool, now ....


Will only dapper packages work on my 6.06 or is there  backwards compatibility ?

Some of the files have [universe] next to them ?  What doe that mean  ? 

Last night I downloaded a file  but it said that I was missing dependancies, I figure that theses are  files  linked to the program I'm trying to install.  

Look, thanks for the  help all and I can't wait till I can return the  favour

Conor

---

### Post by hyper_ch on 2008-04-03
why are you still using 6.06? It's almost 2 years old...

---

### Post by Wim Sturkenboom on 2008-04-03
Yes, and still supported (till 2009 I think) :) That's for me the reason (LTS).

Don't know the reasons of ConorBuzz

---

### Post by ConorBuzz on 2008-04-03
Same  here , Still supported, stable , 

also tried to install 7.10 and it doesn't like  my  graphics card so I can't see anything once I try to install it :(

Also I have a UBUNTU for dummies  book that is based around 6.06. 

If I upgrade to the latest and greatest will it solve any issues for me ?

Regards

Conor

---

### Post by hyper_ch on 2008-04-03
> **ConorBuzz said:**
> If I upgrade to the latest and greatest will it solve any issues for me ?
why don't you try it out yoruself with a desktop cd?

---

### Post by misfitpierce on 2008-04-03
Why not wait 21 more days and try it out with Ubuntu 8.04. It is the newest release that is almost here and guess what... It is a LTS release so you get 3 years of fresh updates :)

---

### Post by ConorBuzz on 2008-04-03
Do new release  have more compatibility ?

Will this assist me in my "No LAN dectected, need drivers  for my WLAN" issue?

Should I just go and buy a new PCI ethernet card, as opposed to the built in one ?

---

### Post by Wim Sturkenboom on 2008-04-09
I would wait for the next LTS (8.04). It might solve the problem. If not, you still have the option to invest the money in another card.

---

### Post by analoog on 2008-04-09
> **ConorBuzz said:**
> 1.Do new release  have more compatibility ?

2. Will this assist me in my "No LAN dectected, need drivers  for my WLAN" issue?

1. yes.
2. nobody knows.

a small hint: a lot of people have problems with their wireless lan, try searching on the forums for a solution, you can use the command lspci (in the terminal) to find oud what wireless card you have. then search for the chipset here.

---

