---
title: "How to Install USB wifi Adapter"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by tyminator on 2007-05-28
So i have read that ndiswrapper is only for x86 architecture. so i am wondering how do PPC users get USB Wifi Adapters to work on ubuntu. I have a Netgear WG111T and i am trying to configure it.  

Please help me out.

---

### Post by stmiller on 2007-05-28
USB adapters that have native Linux drivers work in any Linux (the 'ppc' part is irrelevant). 

Some chipsets like prism and atheros work well, as others. See here:

[http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=91dea4b75666129e4ad59840435ecab9](http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=91dea4b75666129e4ad59840435ecab9)

I think yours is atheros. 

Try

$ sudo modprobe ath_pci

in a terminal before plugging the adapter in.

Type 

$ dmesg

in a terminal to see hw info after it has been plugged in.

---

### Post by tyminator on 2007-05-28
so now i have the realtek driver downloaded but i do not know what to do....

---

### Post by stmiller on 2007-05-29
No, you do not need to download anything (nor does Realtek have PPC Linux drivers, I don't believe). The drivers that work are already there in Ubuntu.

You simply have to type

$ sudo modprobe <driver>

to load the driver.

Try this driver:

$ sudo modprobe r8187

I think that's the realtek driver for this chipset.

---

### Post by tyminator on 2007-05-29
tyler@ubuntu:~$ sudo modprobe r8187
FATAL: Module r8187 not found.

---

### Post by chili555 on 2007-05-30
The r818x module is what you need, I believe. You might try:```
sudo modprobe r818x
```However, this module has been quite troublesome for some users and so, by default, it's blacklisted in Feisty:> # buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187The notations #78255 and #88430 refer to bug numbers open at launchpad, if you interested to read them. I would try the r818x module and see if it causes you any problems. If not, simply comment out the listings in */etc/modprobe.d/blacklist*. Post back and let us know.

---

