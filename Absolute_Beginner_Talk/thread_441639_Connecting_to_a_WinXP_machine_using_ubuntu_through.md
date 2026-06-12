---
title: "Connecting to a WinXP machine using ubuntu through the internet - Choices?"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by saskchi on 2007-05-12
Hello,

I have been using Ubuntu for about three months now and have found it to be reliable and stable. I would like to know if there is a program in Ubuntu that lets me connect to WinXP machines (I usually get calls for tech support from friends).  When I was still using windows I would use an excellent program called Crossloop [http://www.crossloop.com/](http://www.crossloop.com/) . Once installed all the 'Windows' user needed to give me was a access code for me to connect. I did not have to teach them how to forward their ports on their router like RealVNC or any type of configuration.

I can use terminal server client within my own internal LAN and connect to a windows machine (using rdp). I have tried to connect to a windows machine using their IP address on the internet without success. Therefore, this is what I would like to accomplish...

**Goal:** Be able to use Ubuntu to connect to a WinXP machine without the windows user having to install software ...is this possible? I would like to minimize the amount of software/configuration needed on the windows machine for me to connect from the Ubuntu machine.

**Information:** What are other Ubuntu users using to connect to WinXP machines. Is there other choices besides TightVNC, RealVNC etc. Thank you for your input.

P.S. Yes...I have tried to convince the window users to try Ubuntu.

---

### Post by david_kt on 2007-05-13
I just tried crossloop using wine 0.9.36 in ubuntu dapper. It installed and ran without any effort needed. But I do not know whether or not it is functioning as I do not have any computers to connect to.

DK

---

### Post by saskchi on 2007-05-15
Thanks David_tk...

Since I was new to Ubuntu I did not consider WINE. I found out how to install it and found Crossloop to install correctly. I phoned one of my windows friend for a test run...It works! Thanks again David. Hopefully this will help someone.

Therefore,

If you have to connect to a Windows machine to help a user I suggest Crossloop...
1. Get the windows user to install the latest version of Crossloop on their machine (see earlier post for link)
2. Ubuntu user needs to install WINE follow the simple and detailed instructions located in the following link [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
3. Ubuntu user downloads and installs Crossloop
4. Window user connects to Crossloop
5. Ubuntu user connects to Crossloop and can now help out windows user.

A very simple method to help your windows friend until...they switch to Ubuntu :)

---

### Post by ricecom on 2007-09-18
That is fantastic!! The problem for me is in the next step... when my friends are using finally Ubuntu, how do I offer my help with a simple software like Crossloop, is there anything from our community or do I have to install Wine and Crossloop on their machines?? 

Thank you very much for the precious help!!

---

### Post by prosper927 on 2007-12-05
hi there! i love crossloop and now that i am 100% with ubuntu 7.04. can somebody help me on a step by step guide on how to install wine for 7.04 for 64bit AMD?

The only software that I would like to run on top of my ubuntu 7.04 is crossloop.  Hope that there would be anyone here who could guide me on how to realize this step by step. 

Thanks!:guitar:

---

