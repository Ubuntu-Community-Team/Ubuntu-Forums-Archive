---
title: "How to get on to the internet"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Fist of Fury on 2007-08-20
I have been looking around at how to get onto the internet.

My head is buzzing:confused: 

To me that should be easy but I have no idea.

I got a disc for Windows XP, which I shoved in and 2 minutes later I was on.

I would like to keep UBUNTU on my computer but first I would like to be talking to you guys from Ubuntu and not Windows XP

Here, it seems to me, you need a masters degree in computer science to do a simple task like that???

I went here: [http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+to+the+internet](http://ubuntuforums.org/showthread.php?t=91370&highlight=connect+to+the+internet)

Geezus jumping!!!! what anonsense for the casual user.

Giu, Nats, letter for this letters for that...cables from here to there....I just wish someone from the powers that be would write in plain simple English......a go here, click here guide and stop assuming everyone knows how to swap cables around, write script or even knows where to put it when you do write it.

This thing will never take off until it is simplified.

The beginners guide is hardly "windows for dummies"

---

### Post by mysticmatrix on 2007-08-20
First read this
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

and then, since you are only to complain that solution was not for dummies, I guess when the dummy comes we'll help him :)

Cheers

---

### Post by the.phantom on 2007-08-20
you might make it easier if you say
1. how your xp was on the net
2. how you want Ubuntu to be on the net
wireless or what

need details to help you
and what have you tried?

---

### Post by guilly on 2007-08-20
Do us a favour, re read your post and tell me if any one in there right mind can figure out what type of connection issue you are having?

even a windows techy would not have a clue what you are talking about.... (not knocking windows)

you need to add some sort of detail as to what the issue is?

---

### Post by maldojr88 on 2007-08-20
dogs u gotta be a lil more specific....wat type of conection do u wanna get...
because if its a direct conection meaning if its to ur modem or ethernet...its mad quick in linux...
theres barely anything to do...now if its wireless there is a lil work to do but ...
its rewarding once you have it working

---

### Post by ckonrad on 2007-08-20
getting on the internet is pretty easy unless for some reason ubuntu isn't recognizing the proprietary drivers associated within whatever device you are using which isnt the fault of the programmers who created this distribution of linux. 

Are you using a regular dialup modem, ethernet, wireless? Ethernet worked fine for me without any messing around on my laptop however i needed to use a driver wrapper for my wireless card which was a snap to get working. Give some more info so we can help you better.

-corey

---

### Post by mikex on 2007-08-20
Well I'm a newbie linux person myself, but the internet part didn't pose any problems. Generally speaking, the basic settings won't change between Windoze and linux. Look at the settings in windoze and use the same setting in the network setup area in Ubuntu.

---

### Post by Fist of Fury on 2007-08-20
Sorry I was in Urbuntu  trying to figure it out.

I supppose I should have said my connection is a long white wire with a little black box with little green lights on it WAIT!!! that wont do.:)

Billion Bipac ADSL modem..........wan miniport PPPOE 

Thanks for the responses

---

### Post by WebSiteGuru on 2007-08-20
> **Fist of Fury said:**
> Sorry I was in Urbuntu  trying to figure it out.

I supppose I should have said my connection is a long white wire with a little black box with little green lights on it WAIT!!! that wont do.:)

Billion Bipac ADSL modem..........wan miniport PPPOE 

Thanks for the responses

PPPoE telling me that you will need a username and password to login to the internet. (Me thinking here) Does your DSL required you to logon everytime?

---

### Post by Mike-e on 2007-08-20
dunno if this helps or not but im new to linux as well,

had the mad internet issues trying to get it working on edgy, upgraded to fiesty fawn then it was all a plug and play affair

works on both connections through my router, be it usb or ethernet

but all these guy are right so you need to provide more details

---

### Post by bigboy_pdb on 2007-08-20
I looked up "Ubuntu PPPOE" in Google and found the following page:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

In the section "How to configure broadband connections" it mentions that you can use "sudo pppoeconf"

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_broadband_connections](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_configure_broadband_connections)

So in other words open a terminal (Applications -> Accessories -> Terminal) and in it type "sudo pppoeconf" and hit enter. You should be asked for your password and from there you should be able to configure your internet for a PPPOE connection.

---

### Post by Fist of Fury on 2007-08-20
> **WebSiteGuru said:**
> PPPoE telling me that you will need a username and password to login to the internet. (Me thinking here) Does your DSL required you to logon everytime?


Yes it does. I went to properties and checked it out but there was no Ip address and no phone number but I manged to get them from their site [www.trueinternet.co.th](www.trueinternet.co.th).

I tried setting it up in network but when I did it never indicated how you actually log on. Nor did it indicate if it was actually doing anything when I finished.

Bit like when I 1st set it up blank screen for what seemed to be ages and no idea what was happening.

Not the easiest system in the world that's for sure.

---

### Post by PachinCam on 2007-08-30
try this if it works for you - [http://pachinee.homeunix.org](http://pachinee.homeunix.org) 

Good luck,
- A

---

