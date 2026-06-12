---
title: "shutdown -h and -r hang"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by akiratheoni on 2008-04-12
I use Openbox so I don't have a menu item to shut down or restart. So in the past I used 
```
sudo shutdown -h now
```
or
```
sudo shutdown -r now
```

But now neither of them work. It just hangs and does nothing. 

Anything I can do to restore the functionality of these commands? Thanks.

---

### Post by wormser on 2008-04-12
I am unsure why shutdown is hanging.  Are they any type of error messages?  Have you tried the following yet?

```
sudo halt
``````
sudo reboot
```

---

### Post by kerry_s on 2008-04-12
do you have nopasswd in sudoers for shutdown?

other wise it's not hanging it's waiting for the password.

sudo visudo
user    ALL=NOPASSWD: /sbin/shutdown

change "user" to your log in name

mine->

---

### Post by akiratheoni on 2008-04-12
> **kerry_s said:**
> do you have nopasswd in sudoers for shutdown?

other wise it's not hanging it's waiting for the password.

sudo visudo
user    ALL=NOPASSWD: /sbin/shutdown

change "user" to your log in name

mine->

I forgot to mention that it does prompt me for the password. It hangs after I type in the password. Thanks though.

---

### Post by kerry_s on 2008-04-12
> **akiratheoni said:**
> I forgot to mention that it does prompt me for the password. It hangs after I type in the password. Thanks though.

did you try it anyways, so you don't have to type a password?
what are you using (de/wm), that you need use the commands?

---

