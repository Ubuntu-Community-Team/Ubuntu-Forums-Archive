---
title: "US Robotics Sportster Fax Modem Install"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by scaredofnewthings on 2006-03-28
I am a new to Linux and recently installed Ubuntu on my PC.  I have an old US Robotics Fax Modem (005686-03) that I would like to try and use, but have no idea how to install or even where I can find drivers.  All I could find on US Robotics website was an firmware update to v.92, but can't even run that until my modem exists.

Any help would be greatly appreciated.

---

### Post by jason.b.c on 2006-03-28
Is it a com modem??:confused: 

Just plug it in!  ;)  

Then go to i think it's system / networking / modem , or something like that. ( i'm not in ubuntu right now )  Then from there you can **Auto detect modem** and set up your internet connection. :)  

Try that first and see if it works, also i don't think you even need drivers for a serial modem in ubuntu anyway, thats allready built in to the system i'm preaty sure!??:confused:

---

### Post by Kapre on 2006-03-28
Go with jason b.c suggestion - if it is a serial (external modem) it can be detected as soon as the pc starts and the modem is turned ON. You have to go to System----Administration-------Networking and select the modem on the list.

If it is a PCI modem (internal) - then you can search the forum for some more info.

K

---

### Post by scaredofnewthings on 2006-03-30
Thanks jason.b.c and kapre, that was easy.  I would have had to jump through more hoops with the "other" software.

---

### Post by Bartender on 2006-03-30
Were you lucky or was this planned?  The old USR serial modems are just about the easiest modems to use with Ubuntu.  I've got a coupla old beige 0701 Sportster's.  Ubuntu recognized them no sweat.  My ISP doesn't work with Linux at all so I haven't been able to prove that it's working but it appears to be.  Do some Searches for ppp, wvdial, and Modem Monitor.  Those are 3 different programs you can use in Ubuntu to run your modem.  I'm not sure which is best, it appears to be a matter of personal preference.
I also don't know if it makes any difference running the V.92 firmware upgrades from the USR website, but you'll have to do that on a Windows machine.  Might be fun to get the modem running in Ubuntu, get a feel for your connection speed, then install the firmware & try again.

---

### Post by jason.b.c on 2006-03-30
[QUOTE=Bartender]Were you lucky or was this planned?  The old USR serial modems are just about the easiest modems to use with Ubuntu.  I've got a coupla old beige 0701 Sportster's.  Ubuntu recognized them no sweat.  My ISP doesn't work with Linux at all so I haven't been able to prove that it's working but it appears to be.  Do some Searches for ppp, wvdial, and Modem Monitor.  Those are 3 different programs you can use in Ubuntu to run your modem.  I'm not sure which is best, it appears to be a matter of personal preference.
I also don't know if it makes any difference running the V.92 firmware upgrades from the USR website, but you'll have to do that on a Windows machine.  Might be fun to get the modem running in Ubuntu, get a feel for your connection speed, then install the firmware & try again.[/QUOTE]


> My ISP doesn't work with Linux at all 

How could an ISP not work with linux??:confused: , I don't understand that!, in ubuntu there's a part where you have to provide information on what/how you want to connect to the internet. Like phone number to dial, your password, your user name, etc etc..  I think it's PPP config or PPP pon provider in the terminal!:confused:

---

### Post by jason.b.c on 2006-03-30
[QUOTE=scaredofnewthings]Thanks jason.b.c and kapre, that was easy.  I would have had to jump through more hoops with the "other" software.[/QUOTE]


Your welcome..:D

---

### Post by araro23 on 2006-08-10
I just installed Ubuntu on a P3 NEC PC and it detects the Sportster alright but when it dials up on the ISP, it does the regular handshake and then drops/disconnects the connection. Am not sure if I have to edit the program to run at a lower baud rate since I believe the UBUNTU setting is for 115000 something. Am not on my PC right now and will try to see if that works. FYI am very new at Linux (one week) and am still trying to understand "how it works" the editing part.

---

