---
title: "Me and my sodding ATI"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by collierd45 on 2007-12-07
Hallo,

I've just (re)installed Ubuntu 7.10 after seriously screwing my display driver config. I've re-installed the proprietary ATI drivers and everything ***looks*** fine. But I can't enable either the 'normal' or advanced visual effects.

I've attached two screenshots which hopefully should explain it better than I can!

Thanks for your help =]

Lee

---

### Post by skymera on 2007-12-07
to install graphics drivers, i always use Envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

will install nvidia and ati graphics drivers, give that a shot then try effects

---

### Post by overdrank on 2007-12-07
> **collierd45 said:**
> Hallo,

I've just (re)installed Ubuntu 7.10 after seriously screwing my display driver config. I've re-installed the proprietary ATI drivers and everything ***looks*** fine. But I can't enable either the 'normal' or advanced visual effects.

I've attached two screenshots which hopefully should explain it better than I can!

Thanks for your help =]

Lee

Hi and I see by previous post that you are using a ATI 9600. I used the ati driver when I installed gutsy on that system. You can use the fglrx driver but it will slow the system if you do not have enough memory. Hope this helps in some way. good luck!

---

### Post by criskat777 on 2007-12-07
I have a 9600 pro. And don't wast your time the best drivers are the ones that are installed by default in a clean install. I did everything you can think of and the only way i could get 3D Desktop+Compiz-Fusion+Effects and AWN Dock  was by using open source drivers my system is rock solid with not one crash and believe me i have tired to crash it on purpose to see if it would freeze, lockup or crash. the only bad thing is you can't have dual screen. if you setup dual screen you get random freezes.

---

### Post by collierd45 on 2007-12-07
I've just installed the new drivers with Envy to no avail.

Any ideas on any other drivers I could try?

Thanks :)

---

### Post by dashnak on 2007-12-07
With ATI you have to install xserver-xgl before you are able to get desktop effects, this is because ATI does not support AIGLX. Have you tried that already?

---

### Post by Scarath on 2007-12-07
I got an ATI card working using this:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Went from not working at all to allowing all fancy compiz stuff. Hope it helps.

---

