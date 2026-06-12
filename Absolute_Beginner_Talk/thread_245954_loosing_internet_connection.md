---
title: "loosing internet connection"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by edwin_ancaer on 2006-08-28
I'm having the following problem: I regularly seem to loose my internet connection. My question is if there are log files where i could find more information about the cause of this problem.

My browser is Firefox 1.0.8
I'm running Ubuntu 5.10, Breezy Badger. 

Thanks for any information.


Edwin Ancaer

---

### Post by zxee on 2006-08-28
Take a look at /var/log/pppd. How are you connecting to the internet, and how did you set up the connection in the first place?

---

### Post by edwin_ancaer on 2006-08-29
I'm connected via a cablemodem. Is that why I  don't find the file  /var/log/pppd.  

I set up the connection using (at least trying to) the manual from my internet provider. The specifications where for Windows/Mac only, but I think all went very well.

The strange thing is, al can go well for one or two hours, and then suddenly  I seem to have lost the connection, and I need to restart the computer to get it all working again.

I realise there isn't much to base a conclusion on, that's why i'm desperatly looking any error message that could  indicate what's going on.

---

### Post by zxee on 2006-08-30
Take a look at the output of > dmesg <enter> i.e. type the dmesg in a terminal, press the enter key. You may find some message there. Also do a search in the networking section, There are lots of posts there on cable modems.

---

