---
title: "Firestarter won't do start firewall, says device eth0 is not ready?"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-18
I am running 7.10 on a Dell latitude d620. my nic is broadcom wireless.  My wireless internet connection is working fine.

---

### Post by oilchangeguy on 2007-10-18
> **iamthemicrowave said:**
> I am running 7.10 on a Dell latitude d620. my nic is broadcom wireless.  My wireless nterent connection is working fine.

what's a wireless nterent connection? do you mean wireless internet connection? and your title also makes no sense. iptables is ubuntu's firewall, and it runs at startup. firestarter is just the gui.

---

### Post by overdrank on 2007-10-18
> **iamthemicrowave said:**
> I am running 7.10 on a Dell latitude d620. my nic is broadcom wireless.  My wireless nterent connection is working fine.

Please correct me if I am wrong but etho the wired connection. You will need to choose your wifi device. :KS

---

### Post by oilchangeguy on 2007-10-18
> **overdrank said:**
> Please correct me if I am wrong but etho the wired connection. You will need to choose your wifi device. :KS

true. wlan0 is the wireless connection.

---

### Post by overdrank on 2007-10-18
> **iamthemicrowave said:**
> I am running 7.10 on a Dell latitude d620. my nic is broadcom wireless.  My wireless nterent connection is working fine.

Please post back it this has worked or helped you an anyway. :popcorn:

---

### Post by iamthemicrowave on 2007-10-21
Hi everybody, thank you for the help so far.  Now that I am on a wired connection, Firestarter is working.  I went and changed my device to eth1, and now Firestarter will work for my wireless connection.  Is there a way to make it automatically do this?

---

### Post by misfitpierce on 2007-10-21
ehto1 is wireless... switch settings

---

