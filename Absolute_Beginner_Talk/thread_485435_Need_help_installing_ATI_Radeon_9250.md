---
title: "Need help installing ATI Radeon 9250"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Laxton14 on 2007-06-26
hi.. im trying to use Envy to install my ATI radeon 9250 video card.. but i think that it is reading my onboard video card that came with my mother board.. help, please

---

### Post by w4ett on 2007-06-26
Please post the output of :

lspci

and let's see.

---

### Post by starcraft.man on 2007-06-26
> **Laxton14 said:**
> hi.. im trying to use Envy to install my ATI radeon 9250 video card.. but i think that it is reading my onboard video card that came with my mother board.. help, please

Far as I know thats never happened, its usually smart... You did install the card correctly right? I assume you just put it in, to make sure open any terminal and check for its listing in the output of the command "lspci", if its not listed ya got a problem... If it is installed right, I dunno... should defer to the separate card I think.

Edit: Har, w4ett and I had the same thought at the same instant... hehe :D.

---

### Post by w4ett on 2007-06-26
It also depends on the age of the Motherboard...some ot them have a physical jumper.....we just need to go step by step....  :)

BTW, most folks have better luck with the xorg driver ATI and not the proprietary driver for the 9200 and 9250 cards...ATI dropped support for the Legacy Cards...(the 9250 is legacy...sorry)

---

### Post by starcraft.man on 2007-06-26
> **w4ett said:**
> 
BTW, most folks have better luck with the xorg driver ATI and not the proprietary driver....ATI dropped support for the Legacy Cards...(the 9250 is legacy...sorry)

Really? Man, I am so disappointed with ATI them being Canadian and all... they just seem hell bent on shafting their customers.

---

### Post by w4ett on 2007-06-27
> **starcraft.man said:**
> Really? Man, I am so disappointed with ATI them being Canadian and all... they just seem hell bent on shafting their customers.

Yea...it's pretty poor, ATI make such good cards (for MS Windows, anyway), and they are a bit cheaper than Nvidia...I got a stack ot the 9200's that I bought cheap....$4.00 each, New! LOL...just wish their linux support was better!..I had higher hopes for them when AMD bought them  :cry:

---

### Post by cjssmo on 2007-06-27
If you have a newer motherboard some times you can turn off the on board video in the BIOS

---

