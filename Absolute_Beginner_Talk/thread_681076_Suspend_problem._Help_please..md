---
title: "Suspend problem. Help please."
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by DamagePlan on 2008-01-28
When I suspend my system and make it activate again it just stays as a black screen. I got restart the x sever or do anything.

ANy ideas?

THanks

---

### Post by jpittack on 2008-01-28
Please list your graphics card and choosen driver for that card.

---

### Post by emarkd on 2008-01-28
That's a big question as suspend/hibernate are iffy on lots of hardware.  What sort of hardware do you have?  What version of Ubuntu are you using?

---

### Post by DamagePlan on 2008-01-28
Thanks for replies. Anyway im using a hp computer with ubuntu 7.10 installed. I have a radeon graphics card.

---

### Post by macogw on 2008-01-28
What model of radeon?  And what driver are you using?  It's either "ati" or "fglrx".  To see which driver is running, paste the output of:
```
lsmod | grep "radeon\|fglrx"
```

---

### Post by DamagePlan on 2008-01-28
richard@Dyson:~$ lsmod | grep "radeon\|fglrx"
fglrx                1476940  42 
agpgart                35016  2 fglrx,intel_agp
richard@Dyson:~$ 

Ati driver I think


Thanks

---

### Post by macogw on 2008-01-28
Ah ok.  Yeah, that's the binary ATI driver.  The fact that ATI doesn't write drivers that work with suspend is a known issue.  The thing to do is to set the driver to unload when you suspend and reload when you resume.  In /etc/defaults/acpi-support, add "fglrx" to the MODULES line.

---

### Post by DamagePlan on 2008-01-28
ok thankyou.

---

