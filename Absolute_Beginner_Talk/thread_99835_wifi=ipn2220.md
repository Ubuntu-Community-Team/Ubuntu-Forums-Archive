---
title: "wifi=ipn2220"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-06
I have had some help with my wifi problem and I wold like 
to have one last attempt.

dual boot with xp

I downloaded the driver (xp) 


which provide a winxp driver suitable for ndiswrapper, converted it
with

-sudo alien --to-deb driver-ipn2220-2.10.03.2004-1ark.i586.rpm

-and installed the resulting .deb with dpkg -i

when I invoke the command
modprobe ipn2220

cannot find module ipn2220

FOR some strange reason its in 
usr/share/drivers/ipn2220

and not where it should be in 

lib/modules//2.6.12-9-i386/kernel/drivers/net/windows/ipn2220.

I want to know to proceed.

andy:smile:

---

### Post by carlosqueso on 2005-12-06
Alien converts rpm's to debs, windows drivers shouldn't live in either.

If you are trying to use ndiswrapper, you need to download the winXP drivers, which should be in a zip file.  Then unpack it somewhere (doesn't really matter where, but it shouldn't be in your way).  Next, open a terminal, navigate to the place where you unpacked it, and type
```
sudo ndiswrapper -i <driver.inf>
``` where <driver.inf> is the inf file of your driver.  Then type ```
sudo modprobe ndiswrapper
```  let me know if that works.

---

### Post by xstation on 2005-12-07
here's waht I got:



andy108@heis:/usr/share/drivers/ipn2220$ sudo ndiswrapper -i neti2220.inf
Password:
Installing neti2220
andy108@heis:/usr/share/drivers/ipn2220$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
andy108@heis:/usr/share/drivers/ipn2220$ sudo modprobe ndiswrapper
andy108@heis:/usr/share/drivers/ipn2220$





andy:smile: :smile:

---

