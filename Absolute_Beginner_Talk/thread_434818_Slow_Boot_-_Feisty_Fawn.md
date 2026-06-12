---
title: "Slow Boot - Feisty Fawn"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by madapan on 2007-05-06
I was wondering if someone could tell me how to speed up my boot?
I have attached the bootchart and as you can see it is taking 70+ sec to boot compared to 40sec before I upgraded.

Thanks:confused:
PS - If you could tell me in detail because I am a major newbie!!
MUCHO THANKS

---

### Post by starcraft.man on 2007-05-06
> **madapan said:**
> I was wondering if someone could tell me how to speed up my boot?
I have attached the bootchart and as you can see it is taking 70+ sec to boot compared to 40sec before I upgraded.

Thanks:confused:
PS - If you could tell me in detail because I am a major newbie!!
MUCHO THANKS

HOLY!!! How did ya get a boot time that long? Even 40 seconds seems kinda long, I average mostly under 20.

Just a thought, but if it did only begin to occur after you upgraded, I can only surmise that the upgrade might have mixed/messed up certain files >.> Do you have a home parition, if so just reinstall with the live/alternate cd, remount your data and I imagine the problem will dissapear :)

---

### Post by darkROAM_1 on 2007-05-06
Heck, I'm the same boat. I tried the upgrade and it failed, horribly. Use my other box to make a live CD and it works. However, man, that boot takes forever, close to 3 minutes just to boot to login.

---

### Post by starcraft.man on 2007-05-06
> **darkROAM_1 said:**
> Heck, I'm the same boat. I tried the upgrade and it failed, horribly. Use my other box to make a live CD and it works. However, man, that boot takes forever, close to 3 minutes just to boot to login.

wanna post your bootchart too? This is very weird, I also would have thought someone else would have gotten to the first guy since I don't really know whats the cause but maybe there is something in common between ya that is causing this.

---

### Post by darkROAM_1 on 2007-05-06
I hope this worked, not used to attaching files like this. Well, it seems that there is almost no resources being used for the first 2 minutes. hahaha. 

Thanks for the input. :D I'm such a newb.

---

### Post by freebird54 on 2007-05-06
One would assume from the limited information that a hardware detection routine is hanging up something.  Do you have any 'disabled but present' hardware on your setup? A 'not quite connected' USB device?  That is where I would start my troubleshooting if my system got that slow!

---

### Post by madman91 on 2007-05-06
[stupid-question]
how do i get my bootchart?
[/stupid-question]

---

### Post by m0eman on 2007-05-06
> **madman91 said:**
> [stupid-question]
how do i get my bootchart?
[/stupid-question]

lol i was just about to ask that, but i found bootchart on synaptic, im going to install it and try it out.

---

### Post by darkROAM_1 on 2007-05-07
could it honestly be my USB Keyboard and trackball? I'll have to check when I get home. I use wireless on both.

---

### Post by darkROAM_1 on 2007-05-08
Well, new setup, same problems. 

Abit IL9 Pro,
Pentium D 915,
ATI x1300
2gb Patriot 5300 (2x1gb)
120gb EIDE/PATA

And another, new bootchart.

---

### Post by darkROAM_1 on 2007-05-10
hmm, I've re-installed maybe 4-5 times in the last 24 hours from kororaa, pcbsd, kubuntu,sabayon, edgy, and then fesity a few more times. It seems the last couple times, it has booted faster and faster for some reason. 

Now, to get some 3d effects running, I swapped out for a Nvidia 7900gs, runs great now. H ad to strip out my gaming box for it but, hey, maybe it's time to upgrade on that one. :shrug:

---

### Post by ErikTheRed on 2007-05-10
My laptop is booting pretty slowly (this time was 84s). The laptop is not slow by any means though. I have a 1.86ghz Pentium-M and 1gig of RAM. I've attached my bootchart png. Any ideas for me?

---

### Post by charles.figura on 2007-05-11
I had a similar slow boot problem - found out it was my networking trying to bring up a whole host of interfaces.  Since I'm running networkmanager, it can take care of all that stuff, so I edited my /etc/network/interfaces, and commented out everything but the two lines at the top for the loopback.  Now it boots quickly - easily under a minute to Desktop.

---

### Post by dstew on 2007-05-11
Most of the delays I see in the boot charts here are due to dhcp activity, that is, delays in getting networking set up, and this may be the fault of dhcp servers, not the clients. Sometimes this happens if you are trying to initialize ipv6 protocols, and the servers can't handle that, or don't like it for some reason. If you don't need ipv6, you can disable it:

[http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6](http://ubuntuforums.org/showthread.php?t=6841&highlight=disable+ipv6)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

