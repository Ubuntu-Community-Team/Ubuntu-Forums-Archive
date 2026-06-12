---
title: "[SOLVED] Firestarter"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Johnny3 on 2007-09-18
Some people say you don't need a firewall with Ubuntu. But I run firestarter and it blocks a lot of events. If firestsrter did not stop them what would in Ubuntu? Would they just bounce back? 
Thanks Johnny3
Gainesville Fl

---

### Post by w4ett on 2007-09-18
Firestarter is GUI frontend to control iptables in Ubuntu..... it is iptables that is securing your ports:

[http://packages.ubuntu.com/dapper/admin/firestarter](http://packages.ubuntu.com/dapper/admin/firestarter)

---

### Post by tech9 on 2007-09-18
> **w4ett said:**
> Firestarter is GUI frontend to control iptables in Ubuntu..... it is iptables that is securing you ports:

[http://packages.ubuntu.com/dapper/admin/firestarter](http://packages.ubuntu.com/dapper/admin/firestarter)

I agree with w4ett... you don't need firestarter installed... to be secure, its more or less a front-end for you to see whats going on.

---

### Post by Johnny3 on 2007-09-18
I new to this how do you known what ports you have open?
Thanks Johnny3
Gainesville Fl

---

### Post by tech9 on 2007-09-18
> **Johnny3 said:**
> I new to this how do you known what ports you have open?
Thanks Johnny3
Gainesville Fl

Ports are only open when a program that you use accesses the internet. for example FireFox uses internet port 8080. other programs may use any number of ports. 

Install firestarter and monitor this while you are using the system... Otherwise all ports are securely closed

---

### Post by w4ett on 2007-09-18
Here are a couple how-to's :

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

---

### Post by tech9 on 2007-09-18
> **w4ett said:**
> Here are a couple how-to's :

[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

These are good links, if you are not familiar with firestarter.

---

### Post by Johnny3 on 2007-09-18
Thank you. Liking Ubuntu more ever day.
Johnny3
Gainesville Fl

---

### Post by tech9 on 2007-09-19
Your welcome!

Take Care :)

---

### Post by ktdid on 2007-09-19
[SIZE=3]I am a real newbie and have been trying to configure Firestarter for hours.  I now realize I don't need it.  Are there other firewalls that would be recommended for Ubuntu?  BTY, I have only been using Ubuntu for three days, and have it on an external drive.[/SIZE]

---

