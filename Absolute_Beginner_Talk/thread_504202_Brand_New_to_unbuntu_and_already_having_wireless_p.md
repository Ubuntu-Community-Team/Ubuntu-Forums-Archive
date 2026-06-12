---
title: "Brand New to unbuntu and already having wireless problems!!"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by go_appstate on 2007-07-18
OK here is the deal.....I am brand new to Ubuntu and I cannot set up my wireless connection....one more problem, I cannot use a hard wire to connect to the internet to download programs. So the only way I can set things up is by transferring files from another computer by jump drive. My wireless card is a broadcom 4306....from what I hear these cause some problems, probably even more b/c I dont have an ethernet hook up......can some one PLEASE please please help me before i go insane. Thanks!

---

### Post by Dillon on 2007-07-18
I also have a Broadcom wireless modem in my laptop, and I easily fixed the problem by installing the bcm43xx firmware.  I don't remember where i downloaded it from, but it is quite small; about 30kb.  I will attach it to this post if i can find it......

Ahh yes, here we go.. This should fix you up, but if not, you may have to use ndiswrapper.

---

### Post by Yellowdog428 on 2007-07-19
Wow I'm brand new and I can help!

I just did this tonight and [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset") page will get it done for you!

Look at 1.14.5.3

Works like a charm!

Cheers

---

### Post by ukulele_ninja on 2007-07-19
> **Yellowdog428 said:**
> Wow I'm brand new and I can help!

I just did this tonight and [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset") page will get it done for you!

Look at 1.14.5.3

Works like a charm!

Cheers

Hey! Ive been working on this problem for almost 4 days now and that finally solved it! Thank you so much!:guitar:

---

### Post by Dillon on 2007-07-19
If you are using Feisty, you shouldn't have to use the ndiswrapper method.  I will try and find a web page for the firmware i posted...but you should just have to install the .deb package and it should work.  It did for me, and I was really glad to not have to use ndiswrapper.

Found a site for you:

[http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/)

---

### Post by macogw on 2007-07-19
You cant use bcm43xx-fwcutter without a wired connection because it tries to download the firmware from somewhere when you install it.  Unless you can make it extract from the Windows driver and you have that sitting around too.

---

