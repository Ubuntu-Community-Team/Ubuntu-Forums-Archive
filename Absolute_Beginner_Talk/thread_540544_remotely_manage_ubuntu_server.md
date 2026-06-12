---
title: "remotely manage ubuntu server?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-09-01
how can i manage ubuntu server remotely over my network? by manage, i mean like having vnc but for the terminal. so i could execute commands remotely. preferably so it can be done on both linux and windows.

---

### Post by D_2 on 2007-09-01
Do a search for setting up SSH and then you can use a program called PuTTY to get into your server. That is how I do mine. You can also look into using a program called Winmin that lets you do some thigns through HTML style. You would just type in the IP of the server and tell it to use port 10000.

---

### Post by izmaelis on 2007-09-01
> **D_2 said:**
> Do a search for setting up SSH and then you can use a program called PuTTY to get into your server. That is how I do mine. You can also look into using a program called Winmin that lets you do some thigns through HTML style. You would just type in the IP of the server and tell it to use port 10000.

I think you have Webmin, not Winmin, on your mind? Don't you? (-:

---

### Post by Seisen on 2007-09-01
SSH would be the more secure option than VNC.

---

### Post by supersonicdarky on 2007-09-01
ssh works perfectly, thnx =]

---

### Post by HermanAB on 2007-09-01
The de facto standard for managing Linux servers is a combination of SSH, Webmin, Usermin and Virtualmin.  BTW, there are nicer themes available for Virtualmin, since the default look is quite dreadful.

Cheers,

Herman

---

