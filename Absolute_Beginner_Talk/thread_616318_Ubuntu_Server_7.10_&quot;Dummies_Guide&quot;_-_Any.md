---
title: "Ubuntu Server 7.10 &quot;Dummies Guide&quot; - Anyone?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Juice777 on 2007-11-18
HELP!

I'm new to Linux and have decided to setup and install Ubuntu Server 7.10, as a LAMP Server.

The only problem is I can't find any documentation on this site for how to do such things as Login as Root or even Shutdown. All the documentation states is how to use "menus" etc. but all I get is a Unix style command prompt.

Can anyone help?

---

### Post by banewman on 2007-11-18
Have you seen this howto?
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)
As a guide to commands there is this - 
[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)
and for shutdown type - 
sudo shutdown - h now
Hope it gives at least a start :)

---

### Post by Juice777 on 2007-11-18
That's great, but it says I need to be logged in as user "root", when I attempt to login as this user it asks for a password.

Is there a default password Ubuntu gives to the root user?
I haven't set any passwords as yet.

---

### Post by saj0577 on 2007-11-18
```
gksudo nautilus
```

That should have the same effect as login in as root.

Saj

---

### Post by kvonb on 2007-11-18
-

---

### Post by Juice777 on 2007-11-19
A WORKING Internet Connection you say? How do I get one of those?

I have checked /etc/network/interfaces file (which is read-only) and Ubuntu has not picked up my ethernet connection - just shows LOOPBACK and not eth0. Could my server need a network driver? I have checked the HP Website and the only driver available is the bcm5700 lan driver for Red Hat 7.2, will this work on Ubuntu 7.10 server? If so, How do you install drivers? As I can't find any docs on this.

---

### Post by kvonb on 2007-11-20
-

---

