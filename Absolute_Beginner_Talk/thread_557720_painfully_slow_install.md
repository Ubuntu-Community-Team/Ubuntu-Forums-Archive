---
title: "painfully slow install"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by antitheist on 2007-09-23
Unlike probably the vast majority of people who post here, I truly am an absolute beginner so be gentle with me. :p

I have the bare minimum 256 MB of RAM needed to install Ubuntu but of course my PC basically freezes when I get to the second screen of the install (where you choose your location).

I have downloaded and burned 6.06 and then just to double check, ordered the ship its of the officially burned install discs which I checked for errors and there were none detected on either.

So, I am wondering, would the alternate text based install be a good option or should I just buy more RAM?  Has anyone here used the alternate install?  Does it basically give you the same set up process? 

It's not like RAM costs a lot but I am such a technical retard I know I would have a hard time installing more of it without making a mistake.

In any case, I am a very casual PC user with no real knowledge of coding or technology so it is not as if I am dying to use Ubuntu.  I just heard it was in some ways more secure and possibly faster and am interested in trying out. :)

---

### Post by Sef on 2007-09-23
> So, I am wondering, would the alternate text based install be a good option or should I just buy more RAM? Has anyone here used the alternate install? Does it basically give you the same set up process?


I prefer the alternate cd.  Mostly common sense to use it.

Also get more ram: 512 at least.

---

### Post by swisscow on 2007-09-23
Ubuntu may struggle with that Ram, Xubuntu may be better. To be honest, more RAM is the way to go, like you say, it's cheap. And it isn't that difficult to install - you will just need to take the cover off, find the slots for you RAM,make sure you have spare slots availble and then put some new ones in. Of course it isn't that simple - you need to get the right type, so do a little reading first - the motherboard manual would be a good place to start.

---

### Post by wolfen69 on 2007-09-23
i would definitely go for more RAM before all else. but, if that's not possible, yes, the alternate cd is a good choice for a low RAM PC.

---

### Post by PmDematagoda on 2007-09-23
> **antitheist said:**
> Unlike probably the vast majority of people who post here, I truly am an absolute beginner so be gentle with me. :p

I have the bare minimum 256 MB of RAM needed to install Ubuntu but of course my PC basically freezes when I get to the second screen of the install (where you choose your location).

I have downloaded and burned 6.06 and then just to double check, ordered the ship its of the officially burned install discs which I checked for errors and there were none detected on either.

So, I am wondering, would the alternate text based install be a good option or should I just buy more RAM?  Has anyone here used the alternate install?  Does it basically give you the same set up process? 

It's not like RAM costs a lot but I am such a technical retard I know I would have a hard time installing more of it without making a mistake.

In any case, I am a very casual PC user with no real knowledge of coding or technology so it is not as if I am dying to use Ubuntu.  I just heard it was in some ways more secure and possibly faster and am interested in trying out. :)

You can try an Alternate install though I haven't tried it, or do the "quick, but expensive" fix and buy more RAM, fixing the RAM properly is easy, just have a look at the manual you got along with your mainboard and it will be a piece of cake:) Though it may be a waste of money unless you really want to rip Ubuntu up like me;)

---

### Post by antitheist on 2007-09-23
I must say, I appreciate the expedient responses.  I can't recall the last time I posted in an online forum and received so much constructive advice so quickly. :)

So, I think what I am going to do is try the alternate install for now and shop around for RAM tomorrow or the day after when I have the time.

---

### Post by CostaRica on 2007-09-23
I must say that I have installed Ubuntu on two computers with 256Mb of RAM and they work fine.  One of them is a laptop Dell Inspiron 7500 and P3 500MHz (256Mb RAM) and the other one is a clone with an Intel motherboard Celeron 700MHZ with 256Mb RAM and also works fine; not lighting fast but good enough for me.  Today I installed on the last one MySQL 5.0, SPE Python IDE, Inkscape and so.

I am saying this because I do not want this fellow to spend money and then find out that something else was wrong.

What are the other characteristics of the computer, aside from RAM? Brand-model, video card, etc.

If you would rather just buy the RAM and see, that is OK,, but I REALLY doubt that's the reason you can not even FINISH installing it.

Please give us feedback about how everything went.  Good luck!

---

### Post by dptxp on 2007-09-23
Just make a SWAP partition of 1 GB (512MB to 2 GB) using GPARTED (I make it end of the drive)
first.

You shall be be able to install with Live CD.
Ubuntu will run fine.
The SWAP can not be changed during installation.

Worked for me.

---

### Post by antitheist on 2007-09-23
I have not actually bought any new ram or tried the alternate install yet because I was busy today and then wanted to check this post again for new replies before I did either.  I am probably going to buy some much needed RAM regardless, but I do find it interesting that 256 was sufficient for two installs for you, Costa.

> **CostaRica said:**
> What are the other characteristics of the computer, aside from RAM? Brand-model, video card, etc.


Ah, again I have to first remind everyone that is the absolute beginner forum, so bear with me and my ignorance. :)

It is a very modest Dell Dimension desktop with an Intel Celeron 2.53 GHz CPU.  I think the model number might be DE051, but I have no clue what this number signifies really, even after googling around for a while.  Yes, you are seeing the extent of my technical ineptitude in earnest now. :(

As for video card, would that be listed under Device Manager in the windows explorer?  I couldn't find it.  Shocking, I know. :|

I am not sure when it was manufactured; it has been in use for about 14 months now with no problems.



> **dptxp said:**
> Just make a SWAP partition of 1 GB (512MB to 2 GB) using GPARTED (I make it end of the drive)
first.

You shall be be able to install with Live CD.
Ubuntu will run fine.
The SWAP can not be changed during installation.

Worked for me.

This sounds like terrific advice. :)  Er, but of course I had no idea how to actually do this, so after doing some searching I came across the following instructional link:

[http://partedmagic.com/docs/gparted.html](http://partedmagic.com/docs/gparted.html)

Are these instructions basically applicable to Ubuntu 6.06 or is there anything that needs to be adjusted in your opinion?  I admit I am somewhat intimidated by the length of the instructions as it seems to leave some room for error.  If you have any kind of advice with regards to dumbing it down for a technical retard, that would be much appreciated. :KS

---

### Post by dptxp on 2007-09-24
Partitioning is not limited to even Linux, and every Linux uses a SWAP partition.
(You can live without one if you got good amount of RAM).
Here is how to partition-

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 

You will have to make partitions during installation, unless you already have as you need.
You can click on my signature to learn a bit more. Just a bit but useful.

Life will be cool, once you have SWAP ready.

---

