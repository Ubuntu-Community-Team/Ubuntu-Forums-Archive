---
title: "setting up a printer in gusty?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by chrisx16x2008 on 2008-03-13
I wanna add my HP photosmart printer but i am completely lost, people say you have to go system ->administration->printer but i dont know the printers I.P. or name or anything can someone plz help me?

---

### Post by handydan918 on 2008-03-13
What have you tried?
If you want to find the printer, do ```
sudo apt-get install nmap
```

and then nmap 192.168.1/24 (or whatever the network range is on your LAN...)

---

### Post by stchman on 2008-03-13
> **chrisx16x2008 said:**
> I wanna add my HP photosmart printer but i am completely lost, people say you have to go system ->administration->printer but i dont know the printers I.P. or name or anything can someone plz help me?

Is the printer hooked to a network?  If yes then just go to SYstem--->Administration--->Printers and there will be a window with the available network printers.

Select them and you are off.

---

### Post by redgilda on 2008-03-29
I'm trying to set up a printer... the printer is installed on another computer (with Windows). both computers (the printer Win XP and my ubuntu) are connected via the wireless network.. I can see the Win pc on a network (Ive only just installed the latest beta)
When I use the System -> Administration -> Printing -> New printer -> WIndows Printer via SAMBA  --- then I can see the Network MSHOME and the PC but then the printer doesnt show up (both the other Win PC and the printer are on)

any advice? :)

---

### Post by superprash2003 on 2008-03-29
check this out [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by prismpirate on 2008-03-29
If the printer is connected and switched on, then it will list something simliar to HP Photosmart, which should be the name of your printer. Click on it, and follow the instructions to set up your printer

---

### Post by redgilda on 2008-03-30
oh I think it didnt work when I tried to edit my post earlier yesterday. I did manage to get it work! I just kept clicking and it did appear on the list... and it works. prints and stuff. so that was really easy.

It seems like this Samba thingy is included in the Ubuntu general installation and so it was able to recognize the network and the printer - I was really pleasantly surprised. I remember that last time I played around with Ubuntu I had to install it manually.. thanks for any help, appreciated as usual!

---

