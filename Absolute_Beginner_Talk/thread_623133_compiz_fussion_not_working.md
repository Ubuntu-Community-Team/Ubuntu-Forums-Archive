---
title: "compiz fussion not working"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by chris200x9 on 2007-11-25
Hi, I'm fairly new to linux, I am running ubuntu 7.10 on my macbook with intel GMA 950 graphics. I am having a problem with compiz fusion I installed it and only some features worked but I said to myself "it's good enough" then I restarted my computer and none of the features are working.

---

### Post by reesy on 2007-11-25
If you're using Ubuntu  7.10 you shouldn't need to install Compiz fusion it comes pre-installed. Have you installed compizconfig-setting-manager if so try going into there by going to system/ prefrences /advanced desktop effects manager and if not open synaptic package manager and install it.

---

### Post by chris200x9 on 2007-11-25
I have it, It's installed just nothing works. Even when i click the enable nothing will work

---

### Post by reesy on 2007-11-25
Have you gone into System/ Preferences/ Appearance then clicked on visual effects up the top and set in there to custom.

---

### Post by Sinkingships7 on 2007-11-25
> **chris200x9 said:**
> I have it, It's installed just nothing works. Even when i click the enable nothing will work


you might just not have a powerful enough graphics accelerator. the gma 950 is built on-board, and doesn't have all that much power...

---

### Post by chris200x9 on 2007-11-25
> **reesy said:**
> Have you gone into System/ Preferences/ Appearance then clicked on visual effects up the top and set in there to custom.

custom didn't work it just made it so I couldn't move any windows but I put it on extra and it works like a charm :) thank you

---

### Post by reesy on 2007-11-25
Your graphics card can't be able to handle some of the things you've enabled then if you want to customize what effects you have running try disabling them all by going into advanced desktop,  then enable custom in appearance then enable the ones you want in advanced desktop, and if any of them cause your windows to freez again just disable that effect.

---

### Post by Hashimi on 2007-12-12
Can i run compiz fussion with 64 MB intel graphic card ?

---

### Post by jordanmthomas on 2007-12-12
> **Sinkingships7 said:**
> you might just not have a powerful enough graphics accelerator. the gma 950 is built on-board, and doesn't have all that much power...
a 950 is plenty.  I run it on an intel 915 and it runs very well.
> **Hashimi said:**
> Can i run compiz fussion with 64 MB intel graphic card ?
Probably.  What kind is it, exactly?
> Hi, I'm fairly new to linux, I am running ubuntu 7.10 on my macbook with intel GMA 950 graphics. I am having a problem with compiz fusion I installed it and only some features worked but I said to myself "it's good enough" then I restarted my computer and none of the features are working.
What happens if you run
```
compiz --replace
```
from a terminal?

---

### Post by Hashimi on 2007-12-12
Ok i run it successfuly thanks for reply. How can find a complete collection of default commands of Compiz fussion. i searched but couldnt find

---

### Post by jordanmthomas on 2007-12-12
> **Hashimi said:**
> Ok i run it successfuly thanks for reply. How can find a complete collection of default commands of Compiz fussion. i searched but couldnt find

Not sure what you mean here.

---

### Post by Hashimi on 2007-12-12
I mean here; but no matter ; i search google; but couldnt find a complete set.

---

### Post by zabien1970 on 2007-12-12
In the CompizConfig Settings Manager when you click on an object it'll take you to the settings page which will tell you the keystroke combinations, I believe this is what you are referring too

---

### Post by Hashimi on 2007-12-12
> **zabien1970 said:**
> In the CompizConfig Settings Manager when you click on an object it'll take you to the settings page which will tell you the keystroke combinations, I believe this is what you are referring too

Yeah thanks i find it.

---

