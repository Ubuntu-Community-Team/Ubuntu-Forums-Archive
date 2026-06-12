---
title: "Connecting to Internet"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by DoomScythe on 2006-09-03
Hi Ubuntu Community,

I have just installed Ubuntu on my Dell Inspiron 6400 yesterday. I must say that this is a major leap on my part as I am totally new to Lunux and what more Ubuntu. However, I have problems connecting to the Internet and would appreciate help from the gurus of Ubuntu.

I have a CNet ADSL modem (CNAD800AE) which I used to connect to the Internet. I have tried searching for a Linux driver for it but to no avail. Therefore, I was thinking of using the Windows Emulator for Linux, Wine, and install the Windows driver on it. 

My question is, is it all right to install a driver for Windows onto Ubuntu using Wine? If yes, is Ubuntu installed with Wine. Many thanks in advance.

Yours truly,
DoomScythe

---

### Post by CameronCalver on 2006-09-03
ok so im guessing its a broadband modem becuase of the adsl well it should not need a driver try opening up a terminal and typing ping 192.168.1.1 or 
ping 192.168.0.1 and post the results of both the go system administration then eth0 then setting set it to static and set your ipw whatever just do 192.168.1.2 and then leave subnet mask and for default gateway do 192.168.x.x
but replace x with the ping that worked and let me no how u go with that

---

### Post by kombipom on 2006-09-03
Have you tried to connect to the internet?  I think most ADSL modems work without having to add a driver. Mine was set up when I installed and fireffox worked straight away.  Is it connected to an ethernet port or via USB?  If USB can it be connected via ethernet?  If so, try that first.  If it is connected to ethernet look in System->Administration->Networking and try to activate the ethernet connection (and set it as the default gateway).

Hope that this is of some use.

---

### Post by DoomScythe on 2006-09-03
Hi CameronCalver and Kombipom,

Thanks for your quick reply. Well you see, this ADSL modem is connected to my laptop through the USB port and not the NIC. If it was the NIC port, I think it wouldn't give me this problem. To my understanding, anything connected through the USB requires some form of driver.

Anyway, I will try your solution. But first, can you tell me how to open a terminal? I am pretty blank when it comes to networking. :D 

Yours truly,
DoomScythe

---

### Post by mssever on 2006-09-03
To open a terminal, go to Applications > Accessories > Terminal.

---

