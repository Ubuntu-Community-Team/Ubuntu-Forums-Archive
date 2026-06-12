---
title: "wireless feisty on dell b130"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by pellesnusuit on 2007-04-28
Is there a way I can set up drivers for a Dell B130 (Broadcom 1370) using a CD?   I can not get online with a wired connection either.  I can get online with XP wirelessly to get files or driver etc. I am especially new to computers and  I just  burned a feisty Fawn 7.04 and it looks like fun to go online with it. Thanks

---

### Post by deadgobby on 2007-04-28
Please run the ubie live CD and put this command line the the terminal. The terminal can be found at Applications>Terminal
  lspci -v | grep subordinate 
and see if it finds your card. If you get nothing try this command
sudo lshw
 Look for your wireless card and post your findings.

Gobby

---

### Post by pellesnusuit on 2007-04-28
Entered sudo lshw        result was   BCM4318 [AirForceOne 54G]     *-network :1disabled   Thanks for the response Gobby

---

### Post by deadgobby on 2007-04-28
Ugg that one.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

---

### Post by pellesnusuit on 2007-04-28
I'll give it a try.  It will take me sometime. Thank you for help Gobby

---

### Post by deadgobby on 2007-04-28
Take your time and read the directions well. There is some other things we can try, but it not going to easy either. I am happy that you are doing your best.
Gobby

---

