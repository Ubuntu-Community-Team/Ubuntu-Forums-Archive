---
title: "bashrc"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by isandir on 2005-10-22
Hi everyone

I'm attempting to customize my bash shell.  I've done this before in unix.
I was just wondering why there are so many .bashrc's in ubuntu and if any
of them are important.  When i use locate bashrc:

> /etc/skel/.bashrc
/etc/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/bash.bashrc
/usr/share/doc/adduser/examples/adduser.local.conf.examples/skel/dot.bashrc
/usr/share/base-files/dot.bashrc
/home/tim/.bashrc
/root/.bashrc


I'm pretty sure I just want to edit the /home or the /root one to see the 
changes in my terminal, but I was wondering what changing the skel one 
would do.  Thanks!

---

### Post by lcg on 2005-10-22
[QUOTE=isandir]
I'm pretty sure I just want to edit the /home or the /root one to see the 
changes in my terminal,[/QUOTE]
Yes, every user has a personal bashrc in his/her home directory which can be changed by the user.

Aditionally, there's a global bashrc in /etc/bash.bashrc which is used for every user.

[QUOTE=isandir]
but I was wondering what changing the skel one 
would do.  Thanks![/QUOTE]
The files in /etc/skel/ are used as a template for the home directory when a new user is created.

HTH,
Lars

---

