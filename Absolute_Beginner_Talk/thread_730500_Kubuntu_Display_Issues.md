---
title: "Kubuntu Display Issues"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by JuanKawada on 2008-03-20
In kubuntu I've been getting an error where my screen gets completely distorted. The colors are corrupted, there are several colored vertical lines going across the screen, and it seems to repeat itself several times over (I can see the mouse at least 5 times on the same screen). 
This isn't the first time this has happened, but since it was a new install I just reinstalled it before; now I'm getting annoyed. The first time the error happened I was using wine to install a windows game. The second time I was using a game I got from the repositories, and this time I just tried to change my screen resolution. 
I've tried ctrl+alt+backspace, but It doesn't help.  I think maybe if I can change the resolution back It'll fix itself. Can someone tell me how to do this using only the keyboard?

Also If theres a more permanent fix I'd like to hear it, I don't want to be forced to switch back to windows.

---

### Post by JuanKawada on 2008-03-21
bump?

---

### Post by igknighted on 2008-03-21
You should really provide some more information about the hardware involved (monitor/size, graphics card & driver used, what res. you were using and what you changed it to, etc.).

As for games via wine... don't be surprised when they mess stuff up.  Wine is a bonus when it works, but I would never expect it to work.

Also (just for future reference), don't bump a thread until it hasn't been active for 24 hours.  Any shorter just clouds up the forums, and trust me... people do read many pages back.

---

### Post by JuanKawada on 2008-03-21
I'm using an ati radoen 2600 hd pro, I think the drivers were vesa. (If i use the restricted drivers I get this same error).  I'm using a dell monitor thats about 13".

I'm sorry I can't remember what res I was using, but I do know that It was on the highest res possible in the system settings menu. I moved it down one slot. 

I've given up with wine, I'm keeping a windows partition for gaming, and for when I mess up kubuntu. 

Sorry I won't bump again in the future without waiting first.

---

### Post by igknighted on 2008-03-21
> **JuanKawada said:**
> I'm using an ati radoen 2600 hd pro, I think the drivers were vesa. (If i use the restricted drivers I get this same error).  I'm using a dell monitor thats about 13".

I'm sorry I can't remember what res I was using, but I do know that It was on the highest res possible in the system settings menu. I moved it down one slot. 

I've given up with wine, I'm keeping a windows partition for gaming, and for when I mess up kubuntu. 

Sorry I won't bump again in the future without waiting first.

I think support for that card was added to the ATI proprietary drivers (the one the restricted-manager installs) after Gutsy was released (drivers do not get updated after release in ubuntu... thats a debate for another time though).  You can use the Envy tool to install the latest ATI drivers for your card (google for it... I don't remember the website), or try switching to Hardy, which should have a couple drivers that are much better for your card (fglrx, the official ATI driver, as well as radeonhd, a community built driver that is open source and supported by ATI as well)

---

### Post by JuanKawada on 2008-03-21
I'll try Hardy out. Which video driver do you recommend that I use? 

Also, because I've never tried this before, how stable are these beta releases?

---

