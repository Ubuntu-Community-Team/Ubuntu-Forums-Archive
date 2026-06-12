---
title: "How to check the tone in modem?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by My_Ausweis on 2008-01-06
Dear All,

I have modem Conexant HSF1232. I already installed, but when i chose dial up connection using modem,
The modem will dial even though no tone in the line ? how to set the program so it will check the tone first before dialing ?


Thx

L.M

---

### Post by AnonCat on 2008-01-06
When you say installed, do you mean you've installed the drivers or just the modem?  Also, which program are you using to dial out with?  Assuming you're using Wvdial and know how to edit the config file, you might need to add extra lines such as carrier check = no or some others.  Please write more information about the dialing program you're using, the drivers, and whether you're using an internal or external modem.

---

### Post by My_Ausweis on 2008-01-06
I already installed the modem and the driver

---

### Post by yabbadabbadont on 2008-01-06
Try to find where in the program, the modem init strings are stored.  Make sure that "ATX4" is one of the init strings.  If there is a long string of commands starting with AT, just make sure that X4 is in there somewhere.

---

