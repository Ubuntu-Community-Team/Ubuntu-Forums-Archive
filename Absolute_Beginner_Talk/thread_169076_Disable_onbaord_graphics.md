---
title: "Disable onbaord graphics"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by gRiMgRaVy014 on 2006-05-01
I'm having a problem using my Nvidia graphics card when today and idea popped into my head, I thought that the problem might be with me not disabling my onboards graphics, i had it disabled when I used Windoze and I just thought of it. Do you think this is why i can't get Linux to start with my Nvidia card?

---

### Post by Jason_25 on 2006-05-01
You can specify which hardware address you want to use for each device in the xorg.conf.  It would be easier if you just went into your bios and disabled the onboard graphics though.

---

### Post by gRiMgRaVy014 on 2006-05-01
I'll figure I'll just do it from the BIOS because I tried to make it autoconfigure but it just kept finding my onboard grphics and enabling that. But I have a question, if i disable this, Will I still be able to turn it on when its the only graphics card in the machine, liek will it come on by defauly if nothing else is avalibel?

---

### Post by Jason_25 on 2006-05-02
No it won't.  But in that scenario you would just reset your cmos with the jumper.

---

### Post by Rinzwind on 2006-05-02
[QUOTE=gRiMgRaVy014]I'll figure I'll just do it from the BIOS because I tried to make it autoconfigure but it just kept finding my onboard grphics and enabling that. But I have a question, if i disable this, Will I still be able to turn it on when its the only graphics card in the machine, liek will it come on by defauly if nothing else is avalibel?[/QUOTE]
No, before you take out the graphics card you must set the BIOS back to the onboard card 1st. Never forget that.

---

### Post by Jason_25 on 2006-05-02
Resetting the cmos amd going back through the bios settings is really no big deal though.  There are alot of times in which you would need to do that.  Such as if you set a memory timing wrong, etc.

---

