---
title: "video card bus id"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-12-27
I'm trying to find my video card's bus id. I have an nvidia card and when I run lspci -x I get this:

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00: de 10 fd 02 04 04 10 00 a1 00 04 06 08 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 f1 01 00 00
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 00 04 00

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00: de 10 fb 02 07 04 10 00 a1 00 04 06 08 00 01 00
10: 00 00 00 00 00 00 00 00 00 02 02 00 a1 a1 00 00
20: 00 fa f0 fc 01 e0 f1 ef 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 00 1c 00


What do I enter for my bus id?

---

### Post by rajeev1204 on 2006-12-27
why the hell u need ur video bus id?

u probably are trying to install or reconfigure ur graphics card ?

and u typed the command sudo dpkg-reconfigure xserver-xorg ?

if yes then just select default values for whatever u r doing or u will fry ur graphics card


read around in the forums for more info before doing anything like that


regards

rajeev

---

### Post by beamo on 2006-12-27
I'm trying to set up compiz/xgl and every xorg.conf example I see includes the BusId. If it's safe to leave it out I will. I had compiz/xgl running on 6.06 but haven't gotten it to work on 6.10 yet.

---

### Post by rajeev1204 on 2006-12-27
sorry i have no info about compiz or xgl needing bus ids

If reconfiguring xorg just for setting up the graphics card the first time , it is best to leave it to default. 

but for compiz,beryl or XGL i dont know.

u should probably search a bit in the forums


good luck

rajeev

---

