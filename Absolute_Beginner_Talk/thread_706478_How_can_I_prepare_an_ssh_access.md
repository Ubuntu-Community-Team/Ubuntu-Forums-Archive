---
title: "How can I prepare an ssh access?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Usta_AsH on 2008-02-24
Hello I don't know how to do it?

---

### Post by m@ra on 2008-02-24
Humm.. You 
a) connect to your computer from distance 
b) connect to another computer from distance


a)
1. Install a SSH server
 * sudo apt-get install openssh-server*
2.Check your IP 
*(ifconfig)* => And look for inet addr
3. *ssh [email]yourname@your.ip.addr[/email]ess*

b)  *ssh [email]yourname@your.ip.addr[/email]ess*

Let's assume that you have public IP (not starting 192.168.x.x or 10.x.x.x this should be straight forward. If not, u need to make port forward.

But I suggest you also read about hardening / best practices on SSH server.

-markus

---

### Post by Usta_AsH on 2008-02-24
195.174.194.244

can you connect this?

---

