---
title: "how do I get onto the internet?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-10
Hello

Could somebody please tell me how I can get onto the internet?

I don't care if it is wireless or via a cable as long as I get access.

Cheers

---

### Post by reclusivemonkey on 2007-05-10
Do you already have an existing connection with an ISP?

---

### Post by the lemming on 2007-05-10
> **reclusivemonkey said:**
> Do you already have an existing connection with an ISP?


I can connect to the internet when I use XP but not when I use ubuntu or any other linux application

---

### Post by kittyhawk63 on 2007-05-10
What do you use to connect with XP?

---

### Post by the lemming on 2007-05-10
> **kittyhawk63 said:**
> What do you use to connect with XP?



I use a D-Link wireless router DI-524 and a Belkin wireless network card   F5D7000

---

### Post by andrewPCT on 2007-05-10
Can you plug into the router?

---

### Post by the lemming on 2007-05-10
> **andrewPCT said:**
> Can you plug into the router?


I can plug into the router.

Or, I can miss out the router and plug directly into the cable modem but still no joy at getting on-line.

Sadly I do not have any skill or knowledge to tinker around the operating system

---

### Post by crazyclown on 2007-05-10
Plug directly into the router,
Then open a console window and type ifconfig.
You should see two interfaces, you are concerned with the "eth0"
You want to see that this has a UP and an IP address.

I am not setting in front of my KUbuntu box so this is off the top of my head.

---

### Post by the lemming on 2007-05-10
> **crazyclown said:**
> Plug directly into the router,
Then open a console window and type ifconfig.
You should see two interfaces, you are concerned with the "eth0"
You want to see that this has a UP and an IP address.

I am not setting in front of my KUbuntu box so this is off the top of my head.


Those boxes are empty.

How would I go about finding this info?

Also my Router is encrypted with wap but I remember looking somewhere and only seeing a WEP option.

Will this affext matters?

---

### Post by annda on 2007-05-10
if it's OK for you to use a cable connection at first, you don't need to worry about encryption - it is used only for wireless.

are you using edgy or feisty? edgy needs extras for WPA support, feisty supports it out of the box.

---

### Post by crazyclown on 2007-05-13
Press CTRL+ALT+F1
login
then type "ifconfig"
it should list all network interfaces listed 
you are concerned with eth0

---

### Post by totalnub on 2007-05-13
also, this may sound stupid, but shut down, and reboot with the ethernet cable plugged in. sometimes i can't get connected when i hot-plug ethernet. good luck man.

---

