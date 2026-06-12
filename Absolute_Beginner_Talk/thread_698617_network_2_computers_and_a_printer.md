---
title: "network 2 computers and a printer"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by tanyac on 2008-02-16
I have always had a single computer, recently got this new one which i have ubuntu on. 

The desktop which runs ubuntu connects to the internet through a wired connection. from the wall, through my 2wire modem, through my netgear router. the printer is also connected through the desktop directly. 

My laptop connects to the internet through a wireless card and the netgear router. 


What I want to be able to do is access files/move files between the two computers. I also would like to be able to print from the laptop without having to unplug the printer etc.

I have run the windows wizard on my latop. I think I have done what needs to be done with the router. But given my lack of knowledge in this area I cannot figure out what to do with the desktop.

Any help, as detailed yet basic as possible, would be very appreciated.

---

### Post by wolfen69 on 2008-02-16
this may help [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by tanyac on 2008-02-16
thank you, this was helpful.

unfortunately I still cannot get the printer to show up on my laptop. if anyone has any thoughts let me know.

---

### Post by MasterJS on 2008-02-16
If you've set the printer to share from the desktop, then go to SYSTEM > ADMINISTRATION > PRINTING, then hit new printer. If you set it to share through samba,  choose Windows Printer through Samba and browse for it through the server its on (which could be Workgroup or MSHOME) then choose the windows user, and select the printer. On windows you need to go where the printers are shown through the Control Panel, right click it and choose Properties, the Share tab, and set it to share. You should give it a name to help with the sharing. Also when you've chosen your printer, check the box for Authentication Requiered and type guest as the username, no password. Then choose the driver for whatever printer you have and you'll be set.

---

### Post by tanyac on 2008-02-16
This all makes sense to me, but my situation is flipped the other way.

The printer is connected to my desktop which runs ubuntu/samba. My laptop is windows, and I the printer does not seem to be visible through the desktop. i can share files but not the printer. 

i did everything in samba as instructed, so i am not sure what went wrong. 

any help is appreciated, thank you.

---

### Post by MasterJS on 2008-02-16
Have you tried adding the printer? Go to Control Panel > Printers and other devices(something like that) > Printers and Faxes (at the bottom area). Then click add a printer on the left hand side and choose a network printer

---

### Post by tanyac on 2008-02-17
yes i tried that. the printer does not come up when i browse for it, so i cannot add it.

---

### Post by AndyCooll on 2008-02-17
On your Ubuntu desktop, under System > Administration > Printing is your printer set to "Share published printers connected to this system"?

:cool:

---

