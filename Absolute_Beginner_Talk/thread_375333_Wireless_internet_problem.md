---
title: "Wireless internet problem"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by LiquID1232 on 2007-03-03
Hello all. My name is Alex, i have never used Linux before, and have come from Windows.

I've been having trouble with my wireless internet connection. I cant seem to find out how to connect my PC to the one in the front room, thats the computer with the router.

Ive tried the ndiswrapper method, and it didnt seem to work. The driver from my wireless card didnt even install correctly. I've tried everything i can so far. I've read all the guides, searched the fourms.

If there is any thing you can suggest, i would be so gratefull. Im using Ubuntu 6.06 LTS AMD64.

---

### Post by zvezdogled on 2007-03-03
Please post the result of:

lshw -C network

and

iwlist scan

These commands are run in terminal. The first one tels what kind of hard ware do u have for networking and how it is configured. the second one lists all wireless networks that u are receiving and is useful if your card is configured ok.

---

