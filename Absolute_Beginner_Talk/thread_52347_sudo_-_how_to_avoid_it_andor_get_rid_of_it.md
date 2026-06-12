---
title: "sudo - how to avoid it and/or get rid of it"
date: 2005-07-27
forum: Absolute Beginner Talk
---

### Post by supanova on 2005-07-27
Hi All

sudo is fine if you work in an organisation where you define types of Administrators and you painstakingly go through a process of allocating individual rights maybe.... but I dont really see the point for myself.

How do you remove/deactivate it so that you can login directly as root?

After all if you installed your server/desktop and created the user you have full access to the machine anyway and find yourself doing sudo {command} all the time or going sudo su -. It's driving me crazy or am I just missing the point

Thanks

---

### Post by aysiu on 2005-07-27
Surely one of these links may help:

[http://people.ubuntulinux.org/~mako/ubuntu-traffic/u20041126_14.html#9](http://people.ubuntulinux.org/~mako/ubuntu-traffic/u20041126_14.html#9)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1099896833](http://www.ubuntulinux.org/support/documentation/faq/root/talkback/1099896833)

But the basic security strategy with Linux is that you don't want to do anything *accidentally* that can harm your system. Also, if somehow your security gets breached, you want the infecting party to have as little access to your system files as possible.

---

### Post by sonny on 2005-07-27
I strongly recommend (and also 99% of the community) not to run you box as root under any circumstance just if there's no other way, for security resons, as aysiu said, you don't want to accidentally miss-configure you grub file, or you xorg or something else, and you don't want ANYONE to turn on your pc and delete by accident your kernel or stuff like that. If you spend more time using Linux you'll appreciate the sudo command, cuz you know you can leave you little cousin and he won't delete anything by accident nor mess around with your files. There's more than a million reasons not to do what you are attempting to do.

---

### Post by aysiu on 2005-07-27
I also have to say, based on personal experience, now that I have Linux set up, rarely do I have to use root or sudo at all. Sure, if want to update my packages or install new software, I'll use it, but other than that I don't need it to check my email or use the internet (my two primary activities with the computer).

---

### Post by supanova on 2005-07-27
Thanks

All I did was:

sudo su -
passwd

and presto I can su -  

If other people are going to climb on your machine they should simply have their own logon..... I still believe in creating a separate admin user and utilising the user for the bulk of the tasks and only doing an su - when you need to.... 
So what is then so special about sudo... 

Ciao

---

### Post by DJ_Max on 2005-07-27
[QUOTE=supanova]Thanks

All I did was:

sudo su -
passwd

and presto I can su -  

If other people are going to climb on your machine they should simply have their own logon..... I still believe in creating a separate admin user and utilising the user for the bulk of the tasks and only doing an su - when you need to.... 
So what is then so special about sudo... 

Ciao[/QUOTE]
 [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Read the Benefits of sudo and, secuirty part.

---

