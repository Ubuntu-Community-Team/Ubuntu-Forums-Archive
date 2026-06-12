---
title: "linux overheats my laptop help!!!!"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by laurencemulchrone on 2008-01-25
my laptop gets very hot runnign gutsy. are there any software solutions that dnt involve downclocking CPU (its slow as it is)

for example how can i turn on the fans manually because they never come on by themselves.

i am a linux noob and i have no experience with the command line so i would need some detailed help!! i would really appreciate it and i know its alot to ask!! :D

---

### Post by nickpaton on 2008-01-25
What's the make and model of your laptop?

There are a number of posts about this.  Go to Search > Advanced Search and type in 'overheating laptop'.

From the search you will find [this typical post]("http://ubuntuforums.org/showthread.php?t=539365") which may have the solution for you.

To access /etc/ modules, open a terminal Applications > Accessories > Terminal.

Into the terminal type (or copy and paste from here):

```
gksudo gedit /etc/modules
```

and add the lines suggested.  Save and close it and restart the laptop.

Let us know how you get on and good luck!

Nick

---

### Post by zeller on 2008-01-25
How old is the laptop? Ever cleaned it?

First thing I would do is use a vacuum with a hose attachment and suck all the dust out of it.

I was having some similar problems with overheating and a simple vacuuming through my fans kept it from overheating.

If you don't have a vacuum with a hose attachment, try getting your hands on some of that compressed air to blow the dust out of there.

Let us know if these simple steps help first.

---

### Post by FreewheelinFrank on 2008-01-25
How old is the laptop? Has it accumulated a lot of dust in the vents? Try getting a can of compressed air and blasting it through the vents.

Have you Googled the make and model of your laptop to see if anybody else has the same problem?

Is it dual-boot? Do you have the same problem in Windows?

---

### Post by laurencemulchrone on 2008-01-25
thanks for all ur quick responses guys but after using the laptop a bit more i think there is actually a bigger hardware problem with it. i bought it off ebay for 50 quid and it was really temperamental so i got my money refunded. it has 800 mhz (pathetic i no and 256 meg RAM) it works occasionally and i think i will take ur advice and clean it with a vacuum. maybe it will run a bit better.,

overall im not worried to much cuz the laptop was free in the end.

thanks again for ur mulitiple quick replys u guys are a credit to the  community

im gonna get back to my other pc (12.5 GHZ, 4GB corsair RAM, ASUS p5Ne- sli, Nvidia 8600GT, Vista ultimate) 

HOWS THEM FOR SOME SPECS EH??

---

### Post by insane_alien on 2008-01-25
do not use a vacuum cleaner, the difference between one of them and a vande graaf generator isn't as much as you'd think.

open up the case and take a can of compressed air to it.

---

### Post by laurencemulchrone on 2008-01-26
well thanks for letting me know i was literally about to plug the hoover in!!

---

### Post by runemaste644 on 2008-01-26
well, if you ever find a case that would work with your laptop, maybe buy it. One of my desktop computers kept overheating at one time, but a new case fixed it.

---

### Post by nickpaton on 2008-01-26
> **laurencemulchrone said:**
> thanks for all ur quick responses guys but after using the laptop a bit more i think there is actually a bigger hardware problem with it. i bought it off ebay for 50 quid and it was really temperamental so i got my money refunded. it has 800 mhz (pathetic i no and 256 meg RAM) it works occasionally and i think i will take ur advice and clean it with a vacuum. maybe it will run a bit better.,

HOWS THEM FOR SOME SPECS EH??

Hey Laurence there's nought wrong with those specs M8!!  You should be fine with Ubuntu on that - I've set up a number of laptops and desktops with such specs and they run fine.

As to the over heating, yes it would be a very good idea to clean out the fan area.  I've found the best way is to remove the fan assembly which sits over the processor heatsink (quite often towards the rear of the lappy) which comes apart with a couple of screws and then to undo the screw holding the heatsink and fan assembly in place on the mobo.  You will probably find a ton of gunk in the fins, which you can pull out with a pair of tweezers (borrow your sister's!!!!).  Then just blow through and make sure you can see through the fins.  You may also be able to detatch the fan from the fin assembly too, in which case manually clean out the gunk in the blades. 
When replacing it, you may see the remains of some white paste on the flat metal top of the processor.  Ideally you should clean that off with metholated spirits (and the matching surface on the heatsink fin assembly) and replace it with a thin smear of white heatsink paste (available from Maplins and other electronics places in the UK).
A hoover is not the best idea!

Software-wise there is much to look at, and have a search under overheating laptop in advanced search for suggestions or get back to us.

Good luck and stick to the lappy rather than that Ferrari of a PC!!

Nick

---

### Post by laurencemulchrone on 2008-01-26
nick, those specs i was boasting about were for one of my two dektops. i dont have linux on it i was just bbragging :):):)!!!!

i think the notebook, **** as it is, has had it. their are blaitently other hardware problems and i think i will just shove it on ebay for spares and repairs. nice tlkn to all u guys anyway and thanks for all the help!

---

