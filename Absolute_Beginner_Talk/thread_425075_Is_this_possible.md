---
title: "Is this possible"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by tk102570 on 2007-04-27
Hello all, I have just started playing around with Ubuntu. I have a question, is it possible for a windows machine to connect to a system running Ubuntu?

What I mean is if you have two windows machines you can connect one to the other useing this command at the prompt. "net use * \\ip address\c$"  I am sure many people here have used or heard of this command using windows.

Is there anything like this to connect a windows machine to another system running Ubuntu?

Thanks for your help
Tk

---

### Post by Cypher on 2007-04-27
Yes, it's called SAMBA (smbfs) and it will allow you to mount Windows shares on Linux and vice-versa..

---

### Post by monoment on 2007-04-27
Yes, it is possible. Support for connecting to Windows shares comes "out of the box".

You can either mount a share as a smbfs filesystem or automatically mount them by adding the following to /etc/fstab

Read this: [http://us4.samba.org/samba/docs/using_samba/ch05.html](http://us4.samba.org/samba/docs/using_samba/ch05.html)
Pat

---

### Post by Zuph on 2007-04-27
> **tk102570 said:**
> \\ip address\c$

As a side note, I'm not sure if you were just using this as an example or not, but keeping the default system drive share open is terrible security, especially if you're on a public network.

---

