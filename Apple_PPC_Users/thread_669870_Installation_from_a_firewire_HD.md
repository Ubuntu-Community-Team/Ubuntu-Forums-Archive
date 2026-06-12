---
title: "Installation from a firewire HD?"
date: 2008-01-16
forum: Apple PPC Users
---

### Post by Robotriot on 2008-01-16
I have a ibook g3 800mhz with a broken cd drive, do you guys have a way to install ubuntu from a firewire HD like mac os x? Mac os x is giving me trouble, so I was wondering if linux would act better on my hardware.

---

### Post by oswaldkelso on 2008-01-18
Here's a link to how to do a debian net install so I would emagine ubuntu would work in a similar manor

[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

the easy option is to put osx onto the firewire hd and linux on the ppc

[http://www.my2bits.org/?p=81](http://www.my2bits.org/?p=81)

---

### Post by Robotriot on 2008-01-18
im kinda confused.. I dont see where you were going with that.. but I tried installing ubuntu onto a firewire HD and it gives me an error while formatting the HD.. can somebody tell me how to install it to a firewire HD??

---

### Post by stmiller on 2008-01-18
Make sure the drive is connected when you boot from the install CD. Then make sure to pick the external drive as the drive for the install. The ubuntu install will ask the hard drive location during the install.

---

### Post by stream303 on 2008-01-19
> **stmiller said:**
> Make sure the drive is connected when you boot from the install CD. Then make sure to pick the external drive as the drive for the install. The ubuntu install will ask the hard drive location during the install.

Whoa - you just gave me an idea on how to get around that whole yaboot "blessing the drive" situation on external firewire drives.  Even though you can install to an external firewire drive, yaboot always tries to bless the startup boot drive, typically the internal one only.

You can go through a lot of pain to manually bless this new external drive, but if my thinking is correct, the easiest way to do this is to temporarily remove the internal drive, boot with an Ubuntu CD, let it install to the external firewire, which yaboot will then dutifully "bless" since it is the only disk found. You could then reattach your existing internal drive...

Hmmm.. gotta' think on this one.  Mind racing....

Although this doesn't help RobotRiot with his broken CD drive.  The network boot install seems like the best bet, or maybe he can lay his hands on a firewire CD drive temporarily to do the initial install.

---

