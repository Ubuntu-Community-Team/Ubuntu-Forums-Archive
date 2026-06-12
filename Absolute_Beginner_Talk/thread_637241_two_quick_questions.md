---
title: "two quick questions"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-10
alright so i finally got compiz fusion installed on my compter and now i'm trying to make it to where i have like 4 windows or whatever you want to call them so i can make a cube. but when i try to do it it won't do anything...?  do you know how to fix it? (screen shot below) and how do i put awn so that it starts everytime i start my ubuntu?

---

### Post by wormser on 2007-12-10
This [blog]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#") has a great guide for setting the cube up and other effects.

Anytime you want something to start up on boot put it in the session.  System> Preferences> Sessions.

---

### Post by RadiationHazard on 2007-12-10
no i know how to us compiz fusion great! what i'm having a problem with is ubuntu isn't letting me make more than two work spaces like even when i put 4(which is how many i want) or any other number, it simply doesn't do anything. that's what my problem is. not working compiz that's easy.

---

### Post by Teknyk on 2007-12-10
I had to right click the workspace switcher on my panel and then set it to four desktops there.

*EDIT*
right click and go to properties....then set it to four desktops.

---

### Post by RadiationHazard on 2007-12-10
i'm not retarded!! =P goodness i even showed a screen shot showing that i've done that. but it doesn't add anymore work spaces. they just stay at two

---

### Post by RomeReactor on 2007-12-10
Hi. Make sure you have **compizconfig-settings-manager** installed:
```
sudo apt-get install compizconfig-settings-manager
```
After it's installed, you can find it in "System->Preferences->Advanced Desktop Effects Settings"; there, disable the **Desktop Wall** plugin, and enable **Desktop Cube** and **Rotate Cube**.

Also go to **General Options**, and on the **Desktop Size** tab, increase the **Horizontal Virtual Size** to four.

---

### Post by RadiationHazard on 2007-12-10
yep. it says i do and it says it's the latest version.:lolflag:

---

### Post by RadiationHazard on 2007-12-10
anyone here smart enough to answer my question??

---

### Post by akiratheoni on 2007-12-10
> **RadiationHazard said:**
> yep. it says i do and it says it's the latest version.:lolflag:

No need to bump within like ten minutes. If you actually read the posts, you need to configure the desktops in the compizconfig-settings-manager, which RomeReactor stated. Start it by using the command in the Terminal: 

```
ccsm
```

---

### Post by Teknyk on 2007-12-10
Thats where I thought he originally said he adjusted the number of desktops. I completely missed the posted screenshot.
I was changing mine in the effects manager but it still wouldn't give me more than 3 until I changed it on the desktop switcher to 4.

As far as smart enough to answer?
dunno...but I can say my cube works fine. ;)

---

### Post by RadiationHazard on 2007-12-10
haha, nice. well ever since i started dual booting that's when ubuntu started giving me quiet a few problems...

---

### Post by thelatinist on 2007-12-10
**RadiationHazard:**

RomeReactor answered your question perfectly.  To quote him/her:

> **RomeReactor said:**
> Hi. Make sure you have **compizconfig-settings-manager** installed:
```
sudo apt-get install compizconfig-settings-manager
```
After it's installed, you can find it in "System->Preferences->Advanced Desktop Effects Settings"; there, disable the **Desktop Wall** plugin, and enable **Desktop Cube** and **Rotate Cube**.

Also go to **General Options**, and on the **Desktop Size** tab, increase the **Horizontal Virtual Size** to four.

Your rude behaviour is very off-putting, especially when your question has already been answered and you obviously have failed to read the responses you've already been given.  You are much more likely to get help if you ask nicely than if you issue challenges and question the intelligence of the people you want to help you.  Very immature.

---

### Post by wormser on 2007-12-10
> **thelatinist said:**
> **RadiationHazard:**Your rude behaviour is very off-putting, especially when your question has already been answered and you obviously have failed to read the responses you've already been given.  You are much more likely to get help if you ask nicely than if you issue challenges and question the intelligence of the people you want to help you.  Very immature.

I agree.  It is pretty dumb to insult the people trying to help you.  Next time show some respect and rephrase your question better.  If multiple people do not understand then it is probably you.  If you would have read threw my link it gave the directions others posted.  Did that actually work?

---

