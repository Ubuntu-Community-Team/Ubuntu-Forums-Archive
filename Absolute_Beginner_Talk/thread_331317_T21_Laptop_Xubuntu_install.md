---
title: "T21 Laptop Xubuntu install"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by MrGreen on 2007-01-04
Hi,

I have got an old Ibm T21 laptop that I am trying to install Xubuntu on

No real problems installing but I cannot get Xubuntu to start ... I do not get to log in system just freezes

Ok so I tried recovery and I get to root prompt but if I exit it again locks up

Finally I tried startx in recovery mode and X starts but I am running as root [not a good thing]

I can only assume there is a problem with login or startx but I do not know where to start looking 

Any ideas?

MrG

---

### Post by MrGreen on 2007-01-04
I just tried running gdm at root promt and it starts ,,,, 

So I am thinking something before gdm is causing the problem 

MrG

---

### Post by willingc on 2007-01-05
I have a T21 running Ubuntu Edgy 6.10.  I had problems with the video freezing on a black screen before giving me a chance to login.

I made the changes in this article to the xorg.conf file and the GRUB kernel options

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21)

Perhaps this will help you.  Good luck.

Carol

---

### Post by MrGreen on 2007-01-10
Thanks so much I'll give it a go .....

---

### Post by jaripetteri on 2007-01-19
I have Xubuntu Edgy on two T21 Thinkpads without any problems. Otherone is my server ad have been up and running since Edgy was released. Those are both installed on server installation CD and after that installed xubuntu-desktop. And other one is now using even 386 kernel. 

So atleast there is light on the end of the tunel... You may try instaling via server CD?

---

