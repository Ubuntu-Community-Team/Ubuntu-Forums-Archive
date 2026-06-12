---
title: "How do I root?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by cranial-bore on 2006-07-10
Hi,
Just installed Ubuntu. Got the hang of mine sweeper now I want to do something more useful. I'd like to modify the GRUB config to set Windows as the default OS. The commented instructions in the boot file were simple enough but when I tried to save the modified config file I was told I needed root access to do so.

The normal login interface did not allow me to login as root (though I have set a root password). Can someone please tell me how to perform the things that a root, or super user can do?

Also, while I am here -- is it possible to setup different software for different users?
I'd like to install Apache 1.3, PHP4.4 and MySQL 4.1 for one user, and Apache 2, PHP5, MySQL5 for another user. Is this a simple thing to do?

Thanks.

---

### Post by Gustav on 2006-07-10
Ubuntu uses the sudo system, look at this for a explanation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To edit a file as root you use the command 'gksudo gedit <file>' (you can replace gedit with your favourite editor (emacs :)))

---

### Post by FredB on 2006-07-10
> **Gustav said:**
> Ubuntu uses the sudo system, look at this for a explanation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To edit a file as root you use the command 'gksudo gedit <file>' (you can replace gedit with your favourite editor (emacs :)))

Maybe it will be better to plug a topic about root.

And emacs ?!

vim rules !

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

