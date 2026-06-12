---
title: "Internet with dial up"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Axme on 2007-03-13
I am switching to Linux, I have talked the wife around and provided that she can read word docs (Open office) and connect to the internet she is happy with linux. And there is my problem. 
I have a Zoom 3049 external serial modem (bought last week on ebay and working in windows), but I can not figure out how to connect to the internet through ubuntu. The help docs are not that helpful, they just say check that it is compatable (I know it is). Could some one tell me step by step what to do. 
Also, ubuntu uses gnome, can I use Kdevelop with it?

I am using latest ubuntu.

---

### Post by jdfreshwater on 2007-03-13
To help with your dial up issues, I would try to use Gnome-PPP, it has the ability to detect a modem, and seems to do it well.  This may help in setting up your dial up connection.

---

### Post by The Wrecker on 2007-03-13
I'm having the same problem, but with an internal modem. I found the Gnome-PPP.Desktop file, but it looks like a document rather than a application. Where is the Gnome-ppp app located? How do you configure it, or is it pretty easy?

---

### Post by edwardLS on 2007-03-13
I have the Zoom 3049 modem and dialup ISP only.  I found configuring the modem very easy and straight forward.  I am at work now, and the system is at home.  I am using Dapper Drake, and went into System -> Configuration -> Networking.  I enable the Modem device, and permitted the system to autodetect the modem which it did.  I then provided my ISP information, and was off and running.

---

### Post by _duncan_ on 2007-03-13
> I have a Zoom 3049 external serial modem (bought last week on ebay and working in windows), but I can not figure out how to connect to the internet through ubuntu. The help docs are not that helpful, they just say check that it is compatable (I know it is). Could some one tell me step by step what to do.

Click on the 2nd link on my signature (Dial-Up Modem Wiki). It contains a wealth of info on how to get connected using dial-up.

If I remember correctly, the wiki discussed using 3 dialer programs to connect: pppconfig, wvdial and gnome-ppp. Any of the three will do, although I suggest trying out pppconfig or wvdial first since both comes pre-installed with ubuntu by default.

-------------------------------------------------------------

The Wrecker:  Please start a new thread of your own. "Thread-stealing" is generally frowned upon in most forums. It has a way of diluting / stealing attention away from the original poster's (OP) problems.

---

