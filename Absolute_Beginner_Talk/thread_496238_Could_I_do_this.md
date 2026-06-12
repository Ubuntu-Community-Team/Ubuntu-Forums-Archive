---
title: "Could I do this?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by ForensicBroom on 2007-07-08
Well, first of all I have to say I'm very surprised with Ubuntu, just installed it and it works too cool! But, I have a problem. You see, now I'm writing from a PC that has an ATI graphics card (I think it's a Radeon 9200SE), so I should install the drivers for ATI... But the problem is, this isn't my computer. I came here for a couple of days (or maybe a couple of weeks) and brought my hdd with me. I've downloaded Ubuntu, and installed it on my hdd. Now, the problem is I will go home soon, and at home I have a nVidia GeForce FX 5700LE, so my question is, can I install the ATI drivers so I can play with compiz, and then remove them(I have no idea how to do this), and when I get home, install the nVidia drivers? Or is there another solution?
thanks in advance

---

### Post by zek725 on 2007-07-08
I think that's what you should do. I do not know much about virtual machines. I think that's another solution.

---

### Post by dreadlord_chris on 2007-07-08
> **ForensicBroom said:**
> Well, first of all I have to say I'm very surprised with Ubuntu, just installed it and it works too cool! But, I have a problem. You see, now I'm writing from a PC that has an ATI graphics card (I think it's a Radeon 9200SE), so I should install the drivers for ATI... But the problem is, this isn't my computer. I came here for a couple of days (or maybe a couple of weeks) and brought my hdd with me. I've downloaded Ubuntu, and installed it on my hdd. Now, the problem is I will go home soon, and at home I have a nVidia GeForce FX 5700LE, so my question is, can I install the ATI drivers so I can play with compiz, and then remove them(I have no idea how to do this), and when I get home, install the nVidia drivers? Or is there another solution?
thanks in advance

Yup, you sure can. Here's a good place to start:
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by overdrank on 2007-07-08
> **ForensicBroom said:**
> Well, first of all I have to say I'm very surprised with Ubuntu, just installed it and it works too cool! But, I have a problem. You see, now I'm writing from a PC that has an ATI graphics card (I think it's a Radeon 9200SE), so I should install the drivers for ATI... But the problem is, this isn't my computer. I came here for a couple of days (or maybe a couple of weeks) and brought my hdd with me. I've downloaded Ubuntu, and installed it on my hdd. Now, the problem is I will go home soon, and at home I have a nVidia GeForce FX 5700LE, so my question is, can I install the ATI drivers so I can play with compiz, and then remove them(I have no idea how to do this), and when I get home, install the nVidia drivers? Or is there another solution?
thanks in advance

HI and welcome, yes it probably be done but I would recommend not doing so. You are new to ubuntu so take this time to learn the new OS and then when you get home you will have the knowledge and done your research on that card. If you are using feisty, getting beryl to work on the radeon cards can be quite tricky. But that is my opinion. Good luck and welcome.:guitar:

---

### Post by ForensicBroom on 2007-07-08
Now I see I can't because this one is Radeon 9200 and there they say only 9500+ :(  And I was hoping to play with compiz

---

### Post by eternalsword on 2007-07-08
shouldn't be a problem.  you'll want to reconfigure X before you head back though (or maybe you need to do this from safe mode once you get back), so that the generic drivers load, I'm fairly certain vesa will work wherever.  Just make sure you only install the drivers from the repository otherwise it would be very difficult to uninstall.

---

### Post by ForensicBroom on 2007-07-08
> **overdrank said:**
> HI and welcome, yes it probably be done but I would recommend not doing so. You are new to ubuntu so take this time to learn the new OS and then when you get home you will have the knowledge and done your research on that card. If you are using feisty, getting beryl to work on the radeon cards can be quite tricky. But that is my opinion. Good luck and welcome.:guitar:

Well, maybe I am new to ubuntu but I'm a programmer, programming for about 9 years. Only thing in ubuntu that is confusing me are those drivers, because I already tried to install some ATI and they didn't work, had to install ubuntu again :(. The thing that was confusing me, would the ATI drivers work when I get my hard drive to work on my computer. In win xp, if it doesn't work simply go to safe mode and delete the drivers, but here, totally confused :)
Anyway, I found the solution, and now I'm going to test it and see if it works...

here's the link for my solution... hopefully it works :D 
[http://ubuntuforums.org/showthread.php?t=488370](http://ubuntuforums.org/showthread.php?t=488370)

---

### Post by koshari on 2007-07-08
i think it would be easier to take your box in rather than your hdd and vid card, 

but however it wont be hard to change from nvidia to radeon through synaptic, 

keep 2 copies of xorg.conf (one for each card)

---

