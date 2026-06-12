---
title: "Root troubles"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Nathanial042907 on 2007-07-16
I am having some difficulties logging into my Root account. Im using Ubuntu: Dapper. When i go to terminal and type 'sudo -su' or 'sudo -su root' or anything to switch to root. It goes to have me enter my root password. But no matter what it says it is the wrong password. It is correct i have set it in the users configuration. But it still says the password is wrong. Any help on this would be much appreciated.
Thank you
~Nathanial~

---

### Post by charles.g.moore on 2007-07-16
I think the root account is disabled by default if you really want to use su then [http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

I would suggest using sudo exclusivly though...

---

### Post by stchman on 2007-07-16
> **Nathanial042907 said:**
> I am having some difficulties logging into my Root account. Im using Ubuntu: Dapper. When i go to terminal and type 'sudo -su' or 'sudo -su root' or anything to switch to root. It goes to have me enter my root password. But no matter what it says it is the wrong password. It is correct i have set it in the users configuration. But it still says the password is wrong. Any help on this would be much appreciated.
Thank you
~Nathanial~

To get a root terminal type sudo -s.

---

### Post by bodhi.zazen on 2007-07-16
Well, these two are the essentials :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Password is your log-in password (for sudo)

---

### Post by Nathanial042907 on 2007-07-16
Alright once more im sorry to bother you guys but, Im system admin but i need to add fonts. In order to put new fonts in the folders i have to be logged on as "root" now i have logged on root in the terminal but how do i get on the actual user so i can edit the files that only root can edit?
Help Much Apreciated
Thank You
~Nathanial~
P.S. I tried logging on root from loggin screen and it said i cant logon from there

---

### Post by testube_babies on 2007-07-16
All you want to do is add fonts?

[http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/](http://www.smorgasbord.net/2007/06/29/installing-windows-ttf-true-type-fonts-in-linux/)

---

