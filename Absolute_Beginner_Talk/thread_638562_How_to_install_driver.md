---
title: "How to install driver"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by ranjithnair on 2007-12-12
Iam a newbie in linux and I have just recently installed one.i.e,UBUNTU 7.10(with great difficutly in fact!) and I would love use it. I recently downloaded a driver for my modem namely(hsflinmodem-4.06.06.02) and tried to install it using the command 

"sudo apt-get install hsflinmodem-4.06.06.02" The output was

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hsflinmodem-4.06.06.02

Later I tried to install a game,but the result was the same.The game and the driver was in the current directory(\home\ranjith).
Iam a newbie so give very understanding reply. Thanks in advance!!

---

### Post by overdrank on 2007-12-12
> **ranjithnair said:**
> Iam a newbie in linux and I have just recently installed one.i.e,UBUNTU 7.10(with great difficutly in fact!) and I would love use it. I recently downloaded a driver for my modem namely(hsflinmodem-4.06.06.02) and tried to install it using the command 

"sudo apt-get install hsflinmodem-4.06.06.02" The output was

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hsflinmodem-4.06.06.02

Later I tried to install a game,but the result was the same.The game and the driver was in the current directory(\home\ranjith).
Iam a newbie so give very understanding reply. Thanks in advance!!

HI and welcome, I believe you do not need to use apt-get if the files are on your desktop, maybe this link will help
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by t0p on 2007-12-12
You said you downloaded this driver and put it in your home directory, so I take it you didn't get it from the repositories.  Where did you get it from?

If you download stuff from websites, you can't install it with apt-get or Synaptic.  That's why it's best to search Synaptic for stuff you need.  How you install this driver is going to depend on what kind of package it is (eg a .deb, a tarball, etc).  The file name you quoted doesn't tell me what it is I'm afraid.

---

### Post by Sef on 2007-12-12
Have you checked [Linmodems]("http://linmodems.org/")?

---

### Post by bumanie on 2007-12-12
It would be helpful if you state the exact name of the downloaded file. Someone will be able to point you in the right direction once they know what type of file it is.

---

