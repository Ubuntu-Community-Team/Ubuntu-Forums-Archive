---
title: "Firefox suddenly stops working!"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by koz-man on 2007-05-22
I am new to Ubuntu, been using Firefox for long time though in Windows.    Been using Firefox in Ubuntu for 2 weeks with no problems.  Today, even after rebooting, Firefox will NOT open up - no error messages.  Help!

Not sure if these helps but found these errors in System Log: There are more of these but below are just a few:

May 22 07:28:34 jason-laptop kernel: [  281.788000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

May 22 07:22:16 jason-laptop avahi-autoipd(wifi0)[6711]: Successfully dropped root privileges.

E [22/May/2007:07:25:06 -0500] Creating missing directory "/var/run/cups/certs"

---

### Post by taurus on 2007-05-22
Which release are you running and try to run firefox from a terminal so you can post the error message here?

Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by koz-man on 2007-05-22
jason@jason-laptop:~$ firefox
*** CLB *** Initializing Google Browser Sync...
*** CLB *** Instanciating core objects...
*** CLB *** Registering with XPCOM...
*** CLB *** Adding categories...
*** CLB *** Google Browser Sync initialized succesfully!
Segmentation fault (core dumped)


Ubuntu 7.04

---

### Post by koz-man on 2007-05-22
problem resolved: found other post explaining safemode for firefox and addons.

---

