---
title: "how to ssh to my box"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by vertex78 on 2007-08-20
I am trying to learn how to ssh into my desktop from my laptop but am having problems I have ubuntu 7.04 on both machines.  On the desktop i installed openssh-server and firestarter, but I have firestarter stopped, to rule out that being the problem. 

Both machines connect to a linksys router and I have port 22 fowarded to the desktop.  

From my laptop I type ssh 192.168.1.100 but it just hangs
i've also tried ssh -l zach 192.168.1.100 -p 22 and it still hangs

I can ping to the desktop from the laptop with no problems.  Where do I go from here?

---

### Post by Dr Small on 2007-08-20
Try turning ON the firewall and enabling port 22.

---

### Post by janga on 2007-08-20
try > ssh zach@192.168.1.100:22

---

### Post by vertex78 on 2007-08-20
That did the trick.  Is that port closed by default in Ubuntu?

---

### Post by Dr Small on 2007-08-20
I believe so. I just setup my firewall to allow all connections to port 22, and all was fine for me... well, until I changed my ssh port to 56 :p

---

### Post by WebSiteGuru on 2007-08-20
Thanks!, I was just thinking about how to use ssh myself.:popcorn:

---

### Post by Ek0nomik on 2007-08-20
> **vertex78 said:**
> That did the trick.  Is that port closed by default in Ubuntu?

All ports are closed in Ubuntu until a program asks to use the port.

---

### Post by hyper_ch on 2007-08-20
actually, after I installed openssh-server I didn't need to tinker with iptables at all...

I just wonder why it didn't work for you.

---

### Post by bodhi.zazen on 2007-08-20
Here are some helpful links :

1. If you install openssh-server, consider also installing denyhosts

2. Securing ssh : [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

* I like the keys very much

3. general how-to ssh : [http://www.ubuntugeek.com/securely-administer-your-ubuntu-server-remotely.html](http://www.ubuntugeek.com/securely-administer-your-ubuntu-server-remotely.html)

---

### Post by Ek0nomik on 2007-08-20
> **hyper_ch said:**
> actually, after I installed openssh-server I didn't need to tinker with iptables at all...

I just wonder why it didn't work for you.

You shouldn't have to mess around with your iptables at all once you have it installed.  It should start every time you boot into your box and the port will automatically open.

---

