---
title: "Ubuntu Hard Drive Vulnerabilty?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by dogdog on 2008-04-04
I have Ubuntu v7.10 on an older Dell desktop PC and Vista Ultimate on a newer Dell desktop PC. I use cable broadband via a Linksys router. Both PC’s are attached to the router for a LAN. I mainly use the Ubuntu PC to back up files from the Vista PC using automated backup software (Memeo). I have recently noticed, what seems to me, a very odd situation.
The Vista PC is running; the Ubuntu PC is switched on but the user name and password are not yet entered. In this state the software on the Vista PC can backup files to the Ubuntu PC hard drive and retrieve backed up files from the Ubuntu PC.  Does this make sense??
If the Ubuntu PC is switched on but the user name and password are not yet entered what is the status of the Ubuntu O/S?? Is this a Ubuntu vulnerability until the start up process has been completed by entering the user name and password??
If the Ubuntu firewall/iptables are not in place presumably a third party could also access the Ubuntu hard drive via internet access (samba passwords permitting?).
It just seems very odd to me that the Ubuntu hard drive can be accessed at all until the start up/log in process has been fully completed.

---

### Post by jflarm on 2008-04-04
It seems normal to me, because the samba deamon logs in through the network with its own user and password. You don't need a user logged inside the box.
Think of an FTP server or something like that...to think that it won't work without a user logged in makes no sense.
Try googling the issue...it might bring some answers.

---

### Post by hyper_ch on 2008-04-04
Ubuntu/Linux is designed as true multiuser systems.... so you have to differentiate between services that the system runs and your user.

Samba will be a service offered by the system and not by the user so it will be available even if you are not logged in yet.

---

### Post by dogdog on 2008-04-04
Thanks very much for your help. I had not appreciated this.

Two quick queries:

On ubuntu even if user is not logged in I presume that firewall/iptables are in operation?

As an aside do you know if the same applies to Vista PC ie available to network even if user is not logged in?

Many thanks.

---

### Post by hyper_ch on 2008-04-04
> **dogdog said:**
> Thanks very much for your help. I had not appreciated this.

Two quick queries:

On ubuntu even if user is not logged in I presume that firewall/iptables are in operation?

As an aside do you know if the same applies to Vista PC ie available to network even if user is not logged in?

Many thanks.

(1) yes, it is in operation

(2) I don't care about vista...

---

### Post by dogdog on 2008-04-04
Thanks for your help.

You should be more charitable towards Mr Gates. Vista does have its points (hopefully not heresy on a ubuntu forum).

---

