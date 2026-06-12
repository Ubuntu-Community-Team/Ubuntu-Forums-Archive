---
title: "Networking Question"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-06-08
I have my Desktop running with Feisty, I have an External HD that contains my music, movies, work files and such.

Now, I have two Windows XP machines on the same network (One a Laptop, another is a Desktop) they are on the same subnet (addresses respectively 192.168.3.14/192.168.3.15), the Workgroup is MSHOME (as it was created on one of the XP machines.

I can ping the linux system from each of the computers, but once I try to actually connect it asks for my US/PW so I type in my Root US/PW (the one i use to logon) and it doesn't work.

So, my question is what do i need to do.  I have set up networking through system - admin - networks, and installed the (i think it's called) Samba and one other.

What am I missing?

Thx

Seth

P.s. if you need any more info, just ask.

---

### Post by viciouslime on 2007-06-08
You need to set a samba password. For some reason this isn't sync'ed with your account password.

Go to a terminal and type "sudo smbpasswd -a <your username here>" Then enter a password, et voilà :)

EDIT: it should be -a not -u, i have changed the above so it is correct now :)

---

### Post by AlanR8 on 2007-06-08
You might want to have a look at the link below as well. Only found it today and it is easy to follow:

[http://www.dedoimedo.com/computers/linux_commands.html#mozTocId288770](http://www.dedoimedo.com/computers/linux_commands.html#mozTocId288770)

---

### Post by Sethalos on 2007-06-08
Thanks much, I will try this.

Seth

---

