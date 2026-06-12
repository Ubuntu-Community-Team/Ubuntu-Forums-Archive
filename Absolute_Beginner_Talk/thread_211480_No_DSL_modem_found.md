---
title: "No DSL modem found ????"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by 66ekati on 2006-07-08
Good Morning !!!

I am trying a LIVE CD version of " U " it installs fine, but I can't connect to the net... I figure I need to install a PPPoE client for Linux because my ISP uses that protocol.
I have a .tar file on a floppy , is this the best way to install the client ???
I can't see my HD, or files is this supposed to be so ???

So many questions....

Thnaks in advance.

---

### Post by Jucato on 2006-07-08
If you're PPPoE to connect to the internet, you need to run *pppoeconf* on the command line.

Go to Applications > Accessories > Terminal and type in
```
sudo pppoeconf
```
It will attempt to detect your ethernet card, and once successful, it will ask you for your username and password. 

Hope that helps.

---

