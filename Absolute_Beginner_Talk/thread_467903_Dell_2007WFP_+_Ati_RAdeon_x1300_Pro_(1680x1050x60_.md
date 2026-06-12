---
title: "Dell 2007WFP + Ati RAdeon x1300 Pro (1680x1050x60 Resolution)"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by texeRR on 2007-06-08
Hello,
I greatly appreciate your help in advance!
 
My problem: I have the monitor dell 2007wfp and ati radeon x1300 pro graphic card. My default screen resolution is 1680x1050. How should i get this on ubuntu?

I have tried almost every option with editing xorg.conf. but no luck: either the fatal error screen not found or monitor rejection to display something.

The best i could get was: 1280x1024 at 61 Hz with the modification (generic video card, vesa + horizsync 29-81, vertrefresh 59-61).

regards.

---

### Post by Zzl1xndd on 2007-06-08
You'll want to install the proper Video driver, That can be done with the restricted Driver Manager or Via Envy (if you use envy you may need to rerun it on Kernel updates). I use and Nvidia card but there should be a control centre installed with the ATI cards as well that will let you change your res on the fly.

---

### Post by texeRR on 2007-06-08
thanks, tweakedenigma,

I tried the official ati driver [ found here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"). No luck.

regards,

---

### Post by Zzl1xndd on 2007-06-08
here download envy and try to install with this vesa drive you are using now is very basic. but find Envy here run it and auto install the ATI Driver with it. [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by texeRR on 2007-06-12
thanks, tweakedenigma,

For those who have a problem like mine: the wonderful package envy solved indeed my problem.

regards,

---

