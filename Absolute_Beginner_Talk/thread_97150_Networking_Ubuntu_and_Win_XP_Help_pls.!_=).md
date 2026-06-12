---
title: "Networking Ubuntu and Win XP Help pls.! =)"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by unique1 on 2005-11-30
ok, I finally got Ubuntu working on my old PC, now I want to connect it to my current PC with Windows XP through a Lan connection so that I would be able to surf the Net from my Old PC using Ubuntu, can some 1 help me pls. and post the step by step procedure on how to do this. thanks. :)

---

### Post by Mr. Electric Wizard on 2005-11-30
Are you talking about connecting directly to the XP box with a crossover cable, or are you going though a switch/router?

---

### Post by xmorph on 2005-11-30
Hey Unique1,

Theres a few ways to do this, and to make sure I give you the best solution I need to know a little more about your setup.  Do you have a broadband internet connection (Cable/dsl) or ae you using dial-up?

The easiest way if you have a broadband access is to grab a broadband router like this one - [From Linksys.]("http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=c%3DL_Product_C2%26cid%3D1122062340941&pagename=Linksys%2FCommon%2FVisitorWrapper")

It includes a switch with it so the idea is you plug your 2 PC's into it, and your Internet connection and it looks after all connections to the internet for you.  Also heres a good link for some home networking information you may find usefull - [ Home Network How to ]("http://www.pcnineoneone.com/howto/hmnetwk1.html")

---

### Post by Lofticus on 2005-11-30
In my case I set my router to connect to the Internet and as long as I keep connected to my router all my plugged in PC's/Notebooks/Mac's/whatsoevers are connected to the internet.

works fine for me, and most Routers should have the possibility to do so.

---

### Post by unique1 on 2005-11-30
well, I have a DSL connection which is connected directly to my Win XP PC and im planning to connect my Win XP PC with the Ubuntu through A direct cable, any ideas how I can do this, if possible can you pls. post a step-by-step guide, thanks. :)

---

### Post by unique1 on 2005-12-01
Any 1? pls. help me, I really have no clue on how to configure the network in Ubuntu... Help pls. Thanks.

---

### Post by solarcontrol on 2005-12-01
What you are talking about is a VNC type of thing.
You need a VNC server on windows running and giving you permission while you run a VNC client on Linux.

From there you can do what you want on the windows box from the linux box.

For file transfer and folder sharing, use Samba.

Also, you should just spring for a router.
It greatly simplifies everything and theyre cheap nowadays.
Besides, I dont know if Windows will allow a direct cable connection with linux.
It wont even recognize linux partitions on its own drive and LAN (samba-like) networking seems to be it's only hole in this philosophy.

---

### Post by unique1 on 2005-12-01
wow, thanks for saving me a lot of time by telling me straight, not to waste my time. :p  any way, guess ill just buy a router then... :D

---

