---
title: "berly"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by dellboy on 2007-04-03
any one now anything about berly 

what verion of ubuntu dose it work and dose any one else use it 

[http://www.youtube.com/watch?v=MHrT-W7DcNc](http://www.youtube.com/watch?v=MHrT-W7DcNc)

 

this make vista look 5 years old

---

### Post by johnny4north on 2007-04-03
ubuntu 7.04 uses 0.2.1ubuntuI,  just started to use it today.  runs well w/ my nvidia card 4000 128mb,  and 1000 different setting on it.  i dont know to much about it.

---

### Post by dellboy on 2007-04-03
will  Ubuntu 6.06 run it

run or this only for ubuntu 7

---

### Post by igknighted on 2007-04-03
> **dellboy said:**
> will  Ubuntu 6.06 run it

run or this only for ubuntu 7

It is POSSIBLE to run beryl on 6.06, but beryl didn't even exist when 6.06 came out and it isn't intended to be run on systems that old.  You would need to either (a) upgrade your Xorg - not recommended for new users - or (b) install and configure XGL - also no easy task.  If beryl is something that you REALLY want, then upgrade to Edgy or Fesity (in a few weeks), its a two command process in these two.

Note: Beryl is still in the very early stages of development, so there is a high likelyhood that you will run into bugs, some that might even trash your install.  Unless you are willing to accept these risks, don't install beryl.

Note2: What type of video card do you have?  Some provide better drivers than others so your options might be limited by your graphics card brand.

---

### Post by teaker1s on 2007-04-03
pricechild did several beryl howtos, if you look at the sticky in desktop customisation of forums there are links to dapper beryl I believe

---

### Post by dellboy on 2007-04-03
i think it a sis m661mx 

it that that is my video card (is that right)

and  so is Edgy or Fesity ubuntu going to make it easy to add berly  to ubuntu 

and when are they coming out 

i relay thank you for all your help 


thank you 

Dellboy

---

### Post by finferflu on 2007-04-03
Edgy Eft is already out, it's been out for months now. You can [upgrade]("https://help.ubuntu.com/community/EdgyUpgrades") if you want.

Good luck!

---

### Post by anaconda on 2007-04-03
beryl might be too hard to get working in 6.06.. try compiz instead. I think? it will work just fine under 6.06

---

### Post by igknighted on 2007-04-03
> **anaconda said:**
> beryl might be too hard to get working in 6.06.. try compiz instead. I think? it will work just fine under 6.06

Beryl iteslf is easy enough, the issue is Xorg.  The version of Xorg in Dapper doesn't support the kind of compositing needed for AIGLX.  Therefor, no matter what graphics chip or WM of choice, the procedure is the same... XGL.  XGL is certainly not impossible to set up, but it is really easy to mess stuff up permanantly if you don't know what you are doing.  At least with AIGLX you can always apt-get remove beryl && apt-get autoremove and voila, its gone, no harm done.

---

### Post by dellboy on 2007-04-03
> **finferflu said:**
> Edgy Eft is already out, it's been out for months now. You can [upgrade]("https://help.ubuntu.com/community/EdgyUpgrades") if you want.

Good luck!

ok i will update later to this then give berly a shot 

i also thinking of using win4lin for the few thing you need windows for so i dont need to dul boot them both any one use win4lin and got it working 

i will keep you up to data on how it going we berly

---

### Post by dellboy on 2007-04-04
ok i have update to Ubuntu 6.10

that is much better then ubuntu 6.06 

but now how do i got about adding beryl to it 


thank you for your help 

Dellboy

---

