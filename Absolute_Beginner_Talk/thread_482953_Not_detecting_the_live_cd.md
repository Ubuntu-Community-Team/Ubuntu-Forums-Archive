---
title: "Not detecting the live cd"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Cubedude04 on 2007-06-24
Hey, This is my first post so try to go easy on me :)

I have been researching ubuntu for a few months and finally decided to try it. I downloaded a live cd of Dapper Drake so i can see if it supports my hardware and if everything goes well do a full install. 

Now here comes the newb question. 

When i insert the cd upon the computer starting up it either skips right to starting up windows or it gives me a black screen with a flashing _ simple. i have tried pressing delete when the computer is starting up so i can get into bios but it keeps giving me the _ screen

I am sorry if i have posted this on the wrong board 

Oh and i burned the ISO correctly btw and not just copied it over to the cd.

It was burned at 1-2x. And finally i did a checksum before i burned them and it said it was fine.

Thanks in advance :D

---

### Post by atria on 2007-06-24
Welcome to the ubuntu community ;)

I think there are several methods to get into your system BIOs. On some systems its F2 instead of Delete. It should be printed on the screen when it boots, for example press del to enter setup.

I think your boot sequence might be incorrectly configured. Try entering your bios again and ensure that the bootsequence is correctly set to cdrom. Good luck.

---

### Post by Cubedude04 on 2007-06-24
That worked great. I have no idea why i was using delete. 

I am currently using the live cd now and i love it. it's really fast compared to my windows version (and it will get alot faster when i actually install it!)

Thanks again

---

### Post by atria on 2007-06-24
Great it worked, congratulations!

Its my pleasure to help

---

### Post by bigken on 2007-06-24
a few tips if your going to duel boot with windows you must defrag winxp a couple of times and make sure to back up all your imporant data 1st better safe than sorry 

get it installed and have fun :p

---

### Post by jrev on 2007-06-24
after you have done what was suggested before. try & enter the BIOS to adjust the first boot on your DVD reader.
Can you enter the BIOS on your machine ?
solved already ?
Did you start the install ? is it feisty fawn ?

---

### Post by Kosimo on 2007-06-24
> **Cubedude04 said:**
> That worked great. I have no idea why i was using delete. 

I am currently using the live cd now and i love it. it's really fast compared to my windows version (and it will get alot faster when i actually install it!)

Thanks again

Welcome to Ubuntu! :)
By the way, why don't you try to download or get the latest version Feisty Fawn 7.04 ? It's much more stable and have more features than Dapper.  Did you choose the "old" dapper for any special reason maybe?

---

### Post by Cubedude04 on 2007-06-24
I actually do have feisty burned onto a cd ready to install. In the past i had some bad experiences with linux so i decided to burn the live version of dapper to i could check my graphics card, sound card and internet worked properly before installing it

I will probally install feisty tomorrow afternoon. 

and i am not planning to dual boot with windows atm.

Last question 

I read a post the other day that said i should create 3 partitions one for the root, one as swap for virtual memory and another called home for my files

Is this a good idea?

---

### Post by mattg89 on 2007-06-24
Yes, it's a very good idea. The installer does all that for you automatically!

---

### Post by atria on 2007-06-24
It is, because you can backup your files more easily. If you plan to reinstall/upgrade ubuntu in future you can ignore /home and format the root partition only so that your files remain intact.

---

### Post by bigken on 2007-06-24
yes its a very good idea to have seperate home partittion 
if you ever need to reinstall all your file folders and settings
are safe all yyou haave to do is mount it as /home again
without formating 

typical setup is 

10 gig / (root)

twice your ram ie 512mb =1gig swap 

and whats left /home

---

### Post by Cubedude04 on 2007-06-24
Okay sounds great,thanks

---

### Post by Malta paul on 2007-06-24
Hi, I totally agree with whats been said about partitions, in fact I would recommend another extra  partition. This is to keep personal files.
Then if you are like me and screw things up sometimes.  I can boot the live disk and manually format the root ONLY, this then leaves my other partitions with their content intact  :D

---

