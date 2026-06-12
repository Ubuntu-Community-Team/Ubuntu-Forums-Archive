---
title: "Cube - 450Mhz, What's the best Version to install?"
date: 2009-06-07
forum: Apple Hardware Users
---

### Post by teknokrat on 2009-06-07
I am totally new to ubuntu and I bought a CD on ebay with Edgy EFT over a year ago. 
Anyway, I have a Cube 450mhz and I installed it and it's very cool.  I am trying to see if it's faster than the Mac OSX 10.4 that I had running.

My version now is Ubuntu 6.10.

My question is, what is the fastest version I can run on this Cube?  I know that sometimes a newer OS will have more bells and whistles but requires more horsepower.  I want to get the best performance out of this Cube and maybe install it on my kids' iMac G4s since the OSX 10.5 is very slow for them when accessing the web (lots of flash).

Any advice would be appreciated, 

thanks

---

### Post by kerry_s on 2009-06-07
6.10 is old and no longer supported. you can try a newer version:
[http://www.xubuntu.org/get#jaunty](http://www.xubuntu.org/get#jaunty)

but with 450mhz don't expect speed. how much ram do you have?
ram is the important part in linux.

---

### Post by MikeTheC on 2009-06-08
Bear in mind a few things:

1. As far as most Linux distros are concerned, PPC is a red-headed stepchild;

2. Apple PPC hardware support is spotty. Some things work perfectly, but other things have only limited support (video and audio both come to mind, along with wireless, etc.)

3. That machine is fairly low-end, so ideally you should be running XFCE on it as your window manager.

4. I know this is an *Ubuntu* forum, but I would suggest taking a look at either Debian or possibly Fedora. I doubt anything else will run very well on such an old system, if it supports it at all.

---

### Post by roeghar on 2009-06-14
kerry_s, I wouldn't be too discouraged about giving Jaunty a try on your cube. I just finished upgrading a similar machine (PPC G4-digital audio; 466mhz and about 500 megs of ram.) I see no performance drop from the older version (8.04,I think) and everything works as well as can be expected. I'm not expecting things like compiz and 3d rendering to work. The real snag is video, at least in my case. Setting the xorg.conf file correctly is, as far as I can tell, the only way to get the resolution correct. It defaults to like 640x800. And there is almost no entries in the xorg.conf file that is installed with jaunty; the system is supposed to sense what your monitor needs and do the setting. Doesn't work with PPCs. Fortunately, had an old copy of my xorg.conf file and could copy it into the new version. Worked just fine, but I don't no how I would have ever got the setting right without it as there is not a lot of support for this -- at least support that I could understand. So if your upgrading from an earlier version of Ubuntu PPC and your video resolution is right, save a copy where it won't get overwritten. It will save you hours of grief.

---

### Post by kerry_s on 2009-06-14
> **roeghar said:**
> kerry_s, I wouldn't be too discouraged about giving Jaunty a try on your cube. I just finished upgrading a similar machine (PPC G4-digital audio; 466mhz and about 500 megs of ram.) I see no performance drop from the older version (8.04,I think) and everything works as well as can be expected. I'm not expecting things like compiz and 3d rendering to work. The real snag is video, at least in my case. Setting the xorg.conf file correctly is, as far as I can tell, the only way to get the resolution correct. It defaults to like 640x800. And there is almost no entries in the xorg.conf file that is installed with jaunty; the system is supposed to sense what your monitor needs and do the setting. Doesn't work with PPCs. Fortunately, had an old copy of my xorg.conf file and could copy it into the new version. Worked just fine, but I don't no how I would have ever got the setting right without it as there is not a lot of support for this -- at least support that I could understand. So if your upgrading from an earlier version of Ubuntu PPC and your video resolution is right, save a copy where it won't get overwritten. It will save you hours of grief.

:lolflag: i would never buy/own a apple product. just my choice.

---

### Post by roeghar on 2009-06-14
kerry_s, Sorry the message was actually meant for teknokrat, and I was just trying to be helpful. But, kerry_s, as far as your opinion about apple computers, who gives a rip!

---

### Post by kerry_s on 2009-06-14
> **roeghar said:**
> kerry_s, Sorry the message was actually meant for teknokrat, and I was just trying to be helpful. But, kerry_s, as far as your opinion about apple computers, who gives a rip!

:lolflag: i'm just saying, it's no big deal, don't get your panties in a bunch.

---

### Post by evilempire on 2009-06-14
It's just unhelpful and trollish to come into the Apple section and post a random sentence about how you dislike Macs....

---

### Post by kerry_s on 2009-06-14
> **evilempire said:**
> It's just unhelpful and trollish to come into the Apple section and post a random sentence about how you dislike Macs....

who said anything about disliking macs? i like them, i just won't buy or own any apple product for myself. it's a choice i made from my experience dealing with them, they pissed me off that much. i still work on them regularly, there about 60% of the computers i work on upgrading hardware, converting to linux, general repairs, etc...

don't take it wrong guys, i'm not trying to start a fight. i just don't support that company with my money.

---

### Post by cyberdork33 on 2009-06-15
OK... let's just get back on topic... I think that the reply was a result of a mistake on a quote, let's just move on...

---

### Post by roeghar on 2009-06-15
Back to the topic. Another thing I might mention is the experience I had booting from the Jaunty live CD on my G4. At first I really thought it wasn't working. I waited and waited and when nothing happened I ejected it and went on to something else. A few days later I gave it another try and had gone off to pour a cup of coffee when I heard the Ubuntu startup tune from another room. Booting from the CD on these old Macs is really slow. Like I said before, once installed seems as fast as Hardy Herron was.

---

