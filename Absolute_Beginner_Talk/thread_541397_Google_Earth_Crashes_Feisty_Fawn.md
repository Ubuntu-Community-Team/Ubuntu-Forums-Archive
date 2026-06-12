---
title: "Google Earth Crashes Feisty Fawn"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by hkibak on 2007-09-02
I wanted to try the night sky version of Google Earth, so I installed according to [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) and everything behaved normally.  However, when I launched GE for the first time ( Applications --> Internet --> Google Earth) it didn't just CRASH, it booted me clear out to the login screen!!!

I looked back through the help forums and it seems others have had versions of this problem, but mostly no replies to their pleas for help... or solutions written in Martian.  That's why I am in the Absolute-Beginner forum.  

I hope someone has a solution for this or that I have done something stupid, with a simple fix.

Also, I can't seem to find older versions of Google Earth for Linux to try... any suggestions where to look?

---

### Post by MozartlovesUbun2 on 2007-09-02
I can confirm yes it either crashes or freezes my laptop (see specs below)

so is this due to ATi cards?

does anyone know?

---

### Post by daveshields on 2007-09-02
As it happens I had downloaded Google Earth a few minutes ago but hadn't gotten around to installing it.

Prompted by your query, I followed the link cited above and attempted to install GE.

The install went ok, but when I tried to run GE I got a message reporting an "Unknown Graphics Card" error, indicating that GE could not detect an installed graphics card. GE was correct in that I don't have an installed graphics card. I use a motherboard with built-in graphics support, the [http://www.newegg.com/product/product.asp?item=N82E16813135039](http://www.newegg.com/product/product.asp?item=N82E16813135039) , 
ECS GeForce6100SM-M (1.0) AM2 NVIDIA GeForce 6100S Micro ATX AMD Motherboard - Retail

All this suggests that GE has a ways to go before it is ready for prime time on a mature system such as Ubuntu.

So you are not alone in problems with running GE in 7.04.

---

### Post by Duck2006 on 2007-09-02
> All this suggests that GE has a ways to go before it is ready for prime time on a mature system such as Ubuntu.

Works ok on my system.

---

### Post by Detox06 on 2007-09-02
My system it will randomly freeze my gnome. I have found nothing that can seem to fix the issue, and I can't really attach it to GE specifically, but that seems to be the main culprit.. suggestions?

---

### Post by hkibak on 2007-09-02
> **daveshields said:**
> 
All this suggests that GE has a ways to go before it is ready for prime time on a mature system such as Ubuntu.


Yes, I agree with you.  However, the bug is so extreme - the system doesn't just freeze or run slowly, it kicks me off!  I've never had anything like that happen before. I think that this new Night Sky version of GE might just be too beta... but oddly Google's got no more stable versions to play with.  By the way, my system is just a Dell Inspiron 530 that came with Ubuntu installed.  The video card is minimal (128MB NVIDIA GeForce 8300GS) but should be good enough for GE.

---

### Post by hkibak on 2007-09-03
Google Earth 4.2 with Night Sky?!!  I don't know anyone yet who has it working properly on Ubuntu.

---

### Post by oldos2er on 2007-09-03
Google Earth with night sky works fine here. I had the problem of being thrown out of GE too, before I had 3d acceleration turned on (Nvidia card).

---

### Post by swisscow on 2007-09-03
Works fine on my ATI X300.

---

### Post by Zigi15 on 2007-09-06
Doesn't on my Nvidia GeForce Go 7300. Runs fine for some time, then it crashes my Ubuntu with Beryl and I get the dreaded black screen of death. Even Ctrl+Alt+Backspace doesn't fix it completely.

---

### Post by Terl on 2007-09-06
> **Zigi15 said:**
> Doesn't on my Nvidia GeForce Go 7300. Runs fine for some time, then it crashes my Ubuntu with Beryl and I get the dreaded black screen of death. Even Ctrl+Alt+Backspace doesn't fix it completely.

I have noticed that beryl and compiz fusion do not play nice with some apps.  I run it with a 7300LE and have no problems but I use no compiz or beryl.

---

### Post by Steve1961 on 2007-09-06
Seems to be working fine here.  My specs are in my signature.

---

### Post by jryprt on 2007-09-06
> **hkibak said:**
> I wanted to try the night sky version of Google Earth, so I installed according to [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) and everything behaved normally.  However, when I launched GE for the first time ( Applications --> Internet --> Google Earth) it didn't just CRASH, it booted me clear out to the login screen!!!

I looked back through the help forums and it seems others have had versions of this problem, but mostly no replies to their pleas for help... or solutions written in Martian.  That's why I am in the Absolute-Beginner forum.  

I hope someone has a solution for this or that I have done something stupid, with a simple fix.

Also, I can't seem to find older versions of Google Earth for Linux to try... any suggestions where to look?

i just went buy the guide up there & worked fine

---

### Post by J4ym4n on 2007-09-11
I am having the same error -  immediately logs out to the welcome screen.

For my graphics card I have an Nvidia GeForce4 TI 4600

---

### Post by vronp on 2007-09-16
Same problem here.

Running Gutsy on a Dell 9400 Inspiron laptop.

Nvidia GeForce Go 7900 GS

---

### Post by J4ym4n on 2007-09-23
I enabled my graphics driver (was restricted) and Google Earth works without any problems now.

---

### Post by niceguy123 on 2007-10-19
> **J4ym4n said:**
> I enabled my graphics driver (was restricted) and Google Earth works without any problems now.

Thanks, that fixed it for me too. 

But, it also changed my screen resolution (became smaller) and I can't seem to reconfigure now and larger than 800X600.

I'm going to have to un-enable the graphic driver so I can use my whole screen. But then I would be able to use GE.

Any ideas.

---

### Post by galmeida2007 on 2007-10-20
> **hkibak said:**
> I wanted to try the night sky version of Google Earth, so I installed according to [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) and everything behaved normally.  However, when I launched GE for the first time ( Applications --> Internet --> Google Earth) it didn't just CRASH, it booted me clear out to the login screen!!!

I looked back through the help forums and it seems others have had versions of this problem, but mostly no replies to their pleas for help... or solutions written in Martian.  That's why I am in the Absolute-Beginner forum.  

I hope someone has a solution for this or that I have done something stupid, with a simple fix.

Also, I can't seem to find older versions of Google Earth for Linux to try... any suggestions where to look?

I started having the same problem after upgrading to Gutsy. In Feisty Google Earth didn't crash. See my related post in the Desktop Environments forum: "Google Earth crashes and restarts X session"

---

