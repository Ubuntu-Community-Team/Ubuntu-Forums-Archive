---
title: "Connect to Ubuntu From Home"
date: 2007-09-19
forum: Apple Intel Users
---

### Post by Black Mage on 2007-09-19
I'm using a MacBook Pro with OS X 10.4 with developers tools. I was wondering how can I connect to my computer at work(I do know the ip address), log in to Ubuntu, and say work on some Java files or access Eclipse on the work computer?

Basically, I'm trying to get some work done from home on my work computer.

---

### Post by cyberdork33 on 2007-09-19
> **Black Mage said:**
> I'm using a MacBook Pro with OS X 10.4 with developers tools. I was wondering how can I connect to my computer at work(I do know the ip address), log in to Ubuntu, and say work on some Java files or access Eclipse on the work computer?

Basically, I'm trying to get some work done from home on my work computer.

I would start with ssh

---

### Post by ivelasco on 2007-09-20
> **cyberdork33 said:**
> I would start with ssh

I don´t use anything else.That's the best way to login to a linux box.for most security use ssh2 with certificate and root account disabled(only one user account enable).
If you need graphical apps you may call them with
 ssh -X user@host_ip application_name

---

### Post by Black Mage on 2007-09-21
So this code would open VMware Console?

ssh -X john@192.168.1.1  VMware Server Console

Because I get an error saying application does not exist when it does. The VMware server Console is located in my System Tools.

---

### Post by Black Mage on 2007-09-21
Not to computer illiterate(especially command line) idiots like me. I VERY new to Linux.

---

### Post by cyberdork33 on 2007-09-21
> **Black Mage said:**
> Not to computer illiterate(especially command line) idiots like me. I VERY new to Linux.
Don't worry about it. Don't feed the trolls, just report him. 

I can't answer your question though, I have never done that. I use ssh to connect and then tunnel VNC through the ssh connection.

---

