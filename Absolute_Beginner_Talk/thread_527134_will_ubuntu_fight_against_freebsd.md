---
title: "will ubuntu fight against freebsd?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by chongchongworks on 2007-08-16
Hi, I have installed the Freebsd 6.2 in my pc, and just want to make sure whether the ubuntu can recognize the freebsd before installing ubuntu. Because I used to install SUSE in my machine, which cannot recognise Freebsd.

So, if the answer is not ,how can i config it? 

Thanks

---

### Post by hyper_ch on 2007-08-16
Does FreeBSD 6.2 use Grub?

---

### Post by vexorian on 2007-08-16
It won't recognize it , but provided you don't specifically tell the installer to use your freebsd partition it won't wipe it either, you'll have to setup your grub menu.lst to load freebsd, I am sure there are tutorials out there, if not come back and we'll help you.

---

### Post by chongchongworks on 2007-08-17
Sorry, the GRUB u mentioned is like an option menu for multi-boot ?  It can be chosen when we install ubuntu? 

Thanks

---

### Post by Cypher on 2007-08-17
You're going to need to install GRUB to load Linux. GRUB can also boot other OS' like Windows and so on if it knows about it. During Ubuntu installation, you'll come to the GRUB installation screen and it will list all other OS' that it's found and can boot. If FreeBSD is listed good. If not, just go ahead and install GRUB onto the MBR and then when you boot back into Ubuntu, you can modify GRUB to also boot up FreeBSD. From that point onward you'll have a menu choice between these two OS' ..

---

