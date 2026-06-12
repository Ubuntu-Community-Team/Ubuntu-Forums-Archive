---
title: "How can I make the /etc/init.d/rtspserver start permanent?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by arebolledo on 2008-01-08
How can I make the # /etc/init.d/rtspserver start permanent ? Where I have to put this command? Everytime I reboot I lose the information and I have to write it mannualy.

---

### Post by bwhite82 on 2008-01-08
The menu:

System>Preferences>Sessions

Is where you add start-up programs. Is rtspserver in your /usr/bin directory?

---

### Post by arebolledo on 2008-01-08
no it is not, It is on /etc/init.d 

Regards

---

### Post by capink on 2008-01-08
you can symlink to rc2.d ( runlevel 2 directory, which is the default runlevel for ubuntu ):

```
sudo ln -s /etc/init.d/rtspserver /etc/rc2.d/[COLOR="Red"]S99[/COLOR]rtspserver
```

the S99 is mandatory

---

### Post by dcstar on 2008-01-08
> **arebolledo said:**
> How can I make the # /etc/init.d/rtspserver start permanent ? Where I have to put this command? Everytime I reboot I lose the information and I have to write it mannualy.

You have to (as root) create a link to it in the /etc/rc2.d directory, for example:
```
sudo ln -s /etc/init.d/rtspserver /etc/rc2.d/S99rtspserver
```
may well do the job.

---

### Post by arebolledo on 2008-01-08
I did it and I see that the s99rtspserver file is in etc/rc2.d but it doesn't come up...
Regards

---

### Post by capink on 2008-01-08
> **arebolledo said:**
> I did it and I see that the s99rtspserver file is in etc/rc2.d but it doesn't come up...
Regards

the s must be capital S, is it?

---

### Post by arebolledo on 2008-01-09
Capink
the s must be capital S, is it?

you are complete all right, that resolved it, thank you very much for your time.
Regards
arebolledo

---

