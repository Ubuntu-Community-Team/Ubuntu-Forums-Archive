---
title: "wireless ipn2220 --network problems"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by xstation on 2005-12-09
I have had some help with my wifi problem and I wold like
to have one last attempt.

dual boot with xp

I downloaded the driver (xp)


which provide a winxp driver suitable for ndiswrapper, converted it
with

-sudo alien --to-deb driver-ipn2220-2.10.03.2004-1ark.i586.rpm

-and installed the resulting .deb with dpkg -i

then

andy108@heis:/usr/share/drivers/ipn2220$ sudo ndiswrapper -i neti2220.inf
Password:
Installing neti2220
andy108@heis:/usr/share/drivers/ipn2220$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
andy108@heis:/usr/share/drivers/ipn2220$ sudo modprobe ndiswrapper
andy108@heis:/usr/share/drivers/ipn2220$


My wireless card now appears in the network panel
BUT
when I reboot the wireless card dissapears from the network panel.


andy:smile:

---

### Post by Lambert on 2005-12-10
sudo ndiswrapper -m

adds the ndiswrapper module to /etc/modules so its run during startup

---

