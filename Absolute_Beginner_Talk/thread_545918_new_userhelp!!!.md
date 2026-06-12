---
title: "new user?help!!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by bedizma on 2007-09-08
dear all

I am very very basic ubuntu user...I have installed ubuntu and than when i ve try to connect internet ...i couldnt....
somebody said "try to configure your network connection" and do "nano/etc/network/interfaces" and etc...

but how could i do "nano/etc/network/interfaces"...please dont at laugh me i ve said "i am very very basic linux user"

many thanks all your help in advance..

regards

---

### Post by PmDematagoda on 2007-09-08
First of all could you tell me what type of method you were using to connect to the internet such as ADSL, dial-up, wireless, etc.?

---

### Post by forestpixie on 2007-09-08
Welcome to you

> but how could i do "nano/etc/network/interfaces".

when someone tell's you to do things similar to this they'll be talking about using the terminal - you can find it in Apps - Accessories - Terminal

As far as laughing - some might - but ignore them - you've come here for a reason and most people will be extremely helpful. Have fun, don't panic and don't worry too much.

Good luck :D

Edit - while you're feeling new I'd use the Abs Beg Forum - more people look there, it's quite likely you'd get quicker help there

---

### Post by bapoumba on 2007-09-08
Thread moved to "Absolute Beginner Talk".

In addition, nano is a small text editor working from the terminal, you can use it to edit the **/etc/network/interfaces** file. This file is located on the system (or root, or /) partition. You cannot edit it with your regular user permissions. You need to temporarily get admin privilege to do so with **sudo**.

Before you edit the file, please answer the questions, and provide the complete output to (those are two commands to enter in the terminal, you can select the output with the mouse, and middle click to paste it in here):
```
cat /etc/network/interfaces
ifconfig
```

First one lists what is in the current /etc/network/interfaces file, the second will tell how the network is currently configured.

---

