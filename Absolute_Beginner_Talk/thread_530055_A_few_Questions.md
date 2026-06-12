---
title: "A few Questions"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by timelessjazz on 2007-08-20
Today is pretty much been my first day wrestling with Ubuntu 7.04 and I've run into some snags that i'm hoping someone has an answer to.  

First thing is i'm trying to install the Nvidia driver for my 8500GT, and after solving a lot of other issues with it, have now run into the libc header issue and getting a message about having to compile a matching kernel for the driver. I realize there are other posts like this, however i wasn't quite finding the answers i needed. I do not have internet yet on the pc so i can't connect to have it auto download anything for me...which brings me to issue 2

Second, I can only connect to the internet via wireless adapter to a FiOS router.  I can connect to the router fine with the same linksys adapter on my XP laptop, however the ubuntu system will not connect. It is a 64 bit WEB hex encryption, and i know that i'm inputting the info correctly..has anyone had issues like this?

Lastly, I also tried to install ubuntu 6.06 and I kept getting a bios type error, though it was difficult to tell b/c the text was spread all over my display.  I have a ASUS M2N-SLI Deluxe board...is there a known bios issue..i didn't have any luck finding info on this anywhere else.

If anyone could give any help to either of these issues I'd greatly appreciate it! THANKS...

---

### Post by jamvegan on 2007-08-20
> Second, I can only connect to the internet via wireless adapter to a FiOS router. I can connect to the router fine with the same linksys adapter on my XP laptop, however the ubuntu system will not connect. It is a 64 bit WEB hex encryption, and i know that i'm inputting the info correctly..has anyone had issues like this?

I've never been able to get Network Manager to connect with WEP enabled.  I had to install wifi-radar, which works great for me, including WEP and managing multiple locations.  I'm assuming here that Network Manager sees your adapter and your network, but won't connect?

---

### Post by jakev383 on 2007-08-20
Can you give us some more info on the wireless adapter? I used 64bit WEP for years, and just recently decided to use WPA.  Both worked out of the box for me with 7.04. I'm using an Intel 3945ABG card.

---

### Post by timelessjazz on 2007-08-20
The adapter is a Linksys WUSB54G adapter...and I'm connecting to one of those Verizon FiOS routers made by verizon.  The card is detected by ubuntu and I can even see the network i want to connect to when it's in roaming mode...but it won't connect...also it shows no signal from the network, but still detects it...it's def. not a location problem cuz the adapter works w/XP from the same spot.

---

### Post by Wild-eyed-noob on 2007-08-20
I had trouble connecting with the same wireless card and was able to resolve it by going into network settings/ selecting the wireless card/ properties and clearing the check mark in the "enable roaming" .  I had to restart the computer, but then I was able connect.  I don't get the wireless icon on the panel, but it works.
Brad

---

### Post by Hobo Joe on 2007-08-20
Use Envy for installing your drivers.

I have a link in my sig.

---

