---
title: "A couple of questions about all sorts"
date: 2005-09-17
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-09-17
1) I have been trying to get my windows RDC to talk to the linux one and vice versa
On my linux box i get the message no route to host
and on my windows pc i get the 'cient could not connect to remote computer' message. I have enabled the remote connections under preferences but it still doesnt let me in.

2) what does sudo mean, as it doesnt seem to matter if i use it or not?!?!

3) where and how can i get wine, as i need a audio enabled messanger client and was hoping to try messanger or trillian on wine.

---

### Post by aysiu on 2005-09-17
Everything you need to know about sudo:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

For Wine:
```
sudo apt-get update
sudo apt-get install wine
```

---

### Post by weasel fierce on 2005-09-17
sudo is super user. It allows you to do commands that require root access. Try using the apt-get command he posted, without sudo, and you'll propably get a permission error.

---

### Post by dgrafix on 2005-09-17
Thanks thats cleared that up :)
Now all i need to be able to do is view my machine from my laptop using rdc.

---

### Post by cwaldbieser on 2005-09-18
[QUOTE=dgrafix]Thanks thats cleared that up :)
Now all i need to be able to do is view my machine from my laptop using rdc.[/QUOTE]
An RDP (Remote Desktop Protocol) connection will not work from Windows to Ubuntu-- there is no such thing as a GNU/Linux RDP *server* to the best of my knowledge.
Alternative technologies that do basically the same thing are in abundance:  VNC, FreeNX, CygwinX, and (if you like the command line) ssh.

From Ubuntu to your laptop-- first see if you can ping the laptop from Ubuntu:
```
$ ping laptop-IP-address
```
It sounds like you just have a general connectivity issue.  You might just have to update your routing table.  If you cannot ping, post the output of:
```

$ ifconfig
$ route

``` 
and tell us the IP address of your laptop as well.  The first command gives the status of Ubuntu's network cards, the second shows it's routing table.

---

