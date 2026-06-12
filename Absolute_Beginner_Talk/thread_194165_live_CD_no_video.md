---
title: "live CD no video ?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by trollafrogg on 2006-06-11
goes through all the boot motions and then up pops a blank screen with a cursor mark top left corner that cant be written to. 
 if i boot to BIOS and configure primary boot video as onboard video and swap the cable from my Nvidia card to the motherboard the Live CD will boot just fine.

can i set the boot to recognise and use the nvidia card ?

---

### Post by jorn on 2006-06-11
Do I understand you right:
Have you got a videocard on your motherboard and one on your pci or agp port?

---

### Post by trollafrogg on 2006-06-11
yes i have intel graphics chip 810 on the motherboard and a PCI Nvidia Geforce4 420MX card.

---

### Post by jorn on 2006-06-11
I'm not an expert here and I don't know if there are known issues with this card.
I would't bother with this card as long as you use the live-cd. On a real install you could probably install correct drivers.
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I'm not sure about this.

---

### Post by trollafrogg on 2006-06-11
Jorn , thanks for taking an interest. the problem is just the time consuming change over, and i dont want to install just yet, i have a couple years till Vista cancels me out of win.

[edit] i see a special section there just for my card:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

but it says not to follow that page when using the LiveCD ? it would seem it is possible to change something during boot  ?

---

### Post by Xzallion on 2006-06-12
I had that exact same problem.  You can't correct it at boot because you have to be able to log in without the GUI, install the correct drivers for Nvidia (Which isn't hard), restart with the nvidia card and go from there.  I had to use the onboard video to do the install, but all went well from there afterwards.  I would suggest doing a dual boot and get the most out of XP and Ubuntu.  Its just nice being able to use both.

---

