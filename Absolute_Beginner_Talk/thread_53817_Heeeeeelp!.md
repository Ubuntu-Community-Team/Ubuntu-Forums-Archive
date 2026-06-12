---
title: "Heeeeeelp!"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by mimic on 2005-08-02
I need to get my Ubuntu machine to log on to a windows 2000 domain!
any suggestions I am at my wits end ](*,)  ](*,)

---

### Post by sassur on 2005-08-02
The title of your post is extremly stupid to use, insted you should use something like "Help getting Ubuntu to logon to an Win2000 domain". Everybody knows that if you post here you probebly needs help anyway.

Regarding your problem you can probebly find some answers on [http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/).

Sorry for this post but I just felt like ranting a bit.  :wink:

---

### Post by bin on 2005-08-02
I second sassur's comments!

However, if you want to connect to a Windows machine in a domain:-

Places, Server, Windows Share. Put in a name for the connection, the IP address of the machine as opposed to it's name, and the name of the share you want to connect to. A few seconds later yoyu'll get an authentication box - it's upside down compared with normal windows authentication - and for the name you need domain\username not just username. You cannot log on to the domian in the same way as a windows box but you can get to all the shares and services within the limits of your os and user account. Is the domain running Active Directory or is it an NT4 PDC with W2K machines?

---

### Post by mimic on 2005-08-03
Hey thanks guys will give this stuff a try

I did post a thread stating need help connect to a 2000 domain but that had zero replies in a week - so I tried something that would get people wondering!

FYI - server 2000 running Active directory

---

