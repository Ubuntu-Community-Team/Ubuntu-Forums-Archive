---
title: "[SOLVED] Video card wont open"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by N1N31NCHN41L5 on 2008-03-19
I installed qnext on xubuntu and it said that the video card wont open during installation, webcam wont work with any other im or prgram. Have the same problem with Ubuntu recognizing my webcam on laptop. The cam on xubuntu IS supported.

---

### Post by weezy8802 on 2008-03-19
Do you have restricted drivers enabled?

---

### Post by N1N31NCHN41L5 on 2008-03-19
yes i do

---

### Post by N1N31NCHN41L5 on 2008-03-19
i can go to video settings and click on preview and the cam works for like 1 second then locks u. after that preview does nothing till i reload GyachE and it does the same thing over again. smae prob with cam on qnext, skpe etc....

---

### Post by loell on 2008-03-19
can you ```
lsusb
``` in the terminal and paste it here, so we'll know what webcam is this?

---

### Post by N1N31NCHN41L5 on 2008-03-20
josh@xubuntu:~$ lsusb
Bus 001 Device 006: ID 093a:2468 Pixart Imaging, Inc. Easy Snap Snake Eye WebCam
Bus 001 Device 004: ID 059f:0641 LaCie, Ltd 
Bus 001 Device 005: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 003: ID 059b:0155 Iomega Corp. 
Bus 001 Device 002: ID 050d:0237 Belkin Components 
Bus 001 Device 001: ID 0000:0000  
josh@xubuntu:~$ 



there ya go

---

