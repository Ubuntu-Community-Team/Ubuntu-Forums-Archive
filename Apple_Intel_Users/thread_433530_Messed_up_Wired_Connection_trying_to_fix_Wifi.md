---
title: "Messed up Wired Connection trying to fix Wifi"
date: 2007-05-05
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-05
I still have no wireless or sound from speakers.. only head phones


Also.... the GRUB problem where your keyboard is not detected is EXTREMELY annoying... has anyone found a solution?

---

### Post by The_Giver on 2007-05-05
still having same problems =(

---

### Post by depele on 2007-05-05
is your wireless card discoverd?

sound ==> alsamixer and unmute the master channel. You can unmute also other wanted channels.

no idea for the grub
grtz..

---

### Post by The_Giver on 2007-05-05
What do you mean "discovered"???

how do i check that ifconfig?



I think I found a work around for the grub thing though.... I'll keep on testing it and see if it is working.

---

### Post by The_Giver on 2007-05-05
if you mean if i have another mac-address under eth1... then no it is not

---

### Post by The_Giver on 2007-05-05
Well sound works now... thanks.

---

### Post by Chrisj303 on 2007-05-05
There is no soloution for the GRUB issue other than this : USE LILO !

Thats what i did, and the problem is no more.

---

### Post by The_Giver on 2007-05-05
I found a solution I'm satisfied with... but I still can't get damn wireless to work =(

---

### Post by Chrisj303 on 2007-05-05
> **The_Giver said:**
> I found a solution I'm satisfied with... but I still can't get damn wireless to work =(

Really - youve found a way to get to grub to reconise your keyboard at EVERY boot? If so then please tell, because thats a first!

And Wi-Fi - then in your in the right place, stay tuned..


chrisj303

---

### Post by ronocdh on 2007-05-05
> **Chrisj303 said:**
> Really - youve found a way to get to grub to reconise your keyboard at EVERY boot? If so then please tell, because thats a first!

And Wi-Fi - then in your in the right place, stay tuned..


chrisj303
I too would love to hear this miraculous GRUB solution! I've turned to just diddling the arrow keys and stimulating the keyboard enough to keep it awake until GRUB shows up and together we can wreak havoc on its menu options with impunity.

Computers want to be anthropomorphized.

---

### Post by Chrisj303 on 2007-05-05
> **ronocdh said:**
>  I've turned to just diddling the arrow keys and stimulating the keyboard enough to keep it awake until GRUB shows up and together we can wreak havoc on its menu options with impunity.
.

Does that actually work??! 

Why on earth don't you just use LILO!


P.s - under 10mins, i'm getting good. ;)

---

### Post by The_Giver on 2007-05-05
Is there a guide out there.. for installing LILO after you have already used GRUB on the mbp??? I really dont want to mess this up seeing as to how everything but wirless already works

Thanks



PS: The GRUB solution is similar to fiddling with the keys ..... except all you do is wait  on the rEFIT menu for more than 10 seconds (you have 20 seconds until OSX is auto selected) without touching any keys.... then grub should work.. unless its a cold reboot.. you have to restart again (via rEFIT  or w/e/ if you did a cold reboot but most of the time i'm coming from OSX/Linux ).... According to the rEFIT site this is a firmware issue....

---

