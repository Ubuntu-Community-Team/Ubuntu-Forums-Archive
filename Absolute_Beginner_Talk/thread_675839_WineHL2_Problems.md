---
title: "Wine/HL2 Problems"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2008-01-23
So when I run Half-Life 2 in Wine the front screen with the guy and the pipe in his eye comes up very choppy and slow. Takes on average about 2-3 minutes for that screen to show up and go away. After that I have no troubles at all. Is there something I can do to  fix this or speed this up? I'd appreciate any help on this! Thanks! :)

---

### Post by skymera on 2008-01-23
ok what version of wine are you using?

and what is your graphics card?

---

### Post by Tumpster on 2008-01-23
Wine - 0.9.46
Graphics Card - [http://www.newegg.com/Product/Product.aspx?Item=N82E16814150229](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150229)

---

### Post by skymera on 2008-01-23
try updating to 0.9.53, runs team fortress 2 really good.

have you got the correct driver installed?
if so, how was it installed?

---

### Post by Tumpster on 2008-01-23
> **skymera said:**
> try updating to 0.9.53, runs team fortress 2 really good.

have you got the correct driver installed?
if so, how was it installed?

Yes, I've got all my drivers loaded and running just fine, I'm running Gutsy so I had to have all things tweaked out for Compiz fun. I installed it through Automatix2 but then updated recently to 0.9.53 as you suggested, still happens. Things in half-life 2 are very bright and dark pending what it is and my flashlight doesn't work Any ideas?

---

### Post by skymera on 2008-01-24
so your running the game WITH compiz running?

try

ALT+F2
metacity --replace

then try the game.
plus i wouldnt use Automatix. Know to break systems.

---

### Post by rhc on 2008-01-24
if the thing that skymera said

metacity --replace 

doesn't work,delete "xserver-xgl" from Synaptic.

---

### Post by Tumpster on 2008-01-24
> **rhc said:**
> if the thing that skymera said

metacity --replace 

doesn't work,delete "xserver-xgl" from Synaptic.

What does deleting xserver-xgl do?



Also tried the metacity one and it didn't work, still ran choppy.

---

### Post by rhc on 2008-01-24
Xgl gives you all that eye candy effects on compiz.
If you delete it 3d dekstop effects ll be gone.
But anytime you can install it again.
It ll take 15 seconds.

Actually metacity --replace should solve your problem but i heard that some people only take good performance after deleting Xgl.

---

### Post by skymera on 2008-01-24
i dont have xserver-xgl

and i run compiz =S

---

### Post by Tumpster on 2008-01-25
What should I do then? Is this just a bug I deal with or is there an alternative?

---

### Post by skymera on 2008-01-25
have you removed xserver-xgl?

restart, if nothing happens when you login reinstall it.

---

### Post by Tumpster on 2008-01-30
So still when I start up HL2 the valve screen and the credis before you get to the main screen run reaaallllyyyy slow and choppy. After this the game plays just fine, except things are brighter until you use them or are on top of em, I have no flashlight that works, windows seem to display as triangles, and items fade away and back in as i'm walking.
I'm running an nvidia xfx 8600gt xxx edition with wine 0.9.54 and the latest drivers and Ubuntu Gutsy. Thanks for any help! :)

---

### Post by Tumpster on 2008-02-02
ANyone?

---

### Post by randy78 on 2008-02-02
Well, it might be a Wine compatibility issue...
Try configuring Wine to run as Windows XP in the Applications tab...

This has solved several problems for me so you might give it a shot...

It almost sounds like you have accidentally entered a Debug mode in the game.

Let us know if you get this solved and be sure to mark the title of your post as SOLVED too, so others can use the information!

---

