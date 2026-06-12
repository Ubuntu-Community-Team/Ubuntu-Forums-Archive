---
title: "Stuck in grub after fresh install 9.10 - pls help"
date: 2009-11-13
forum: Apple Hardware Users
---

### Post by EvansFive on 2009-11-13
After having a few issues I did a fresh install of 9.10 on my iMac.

It all finished ok and then wanted to restart.

It came up to rEFIt and I selected the Legacy OS option and it said Starting Stage 2

Then just displayed the "GRUB> " prompt and would not list the options to boot from.

I am totally stuck!!

Could someone please direct me to how to get this thing booting?

---

### Post by Ravernomina on 2009-11-13
Hey ^_^. Give this a shot. 

Boot rEFIt
click on the partition tools
sync partitions
restart
try loading grub then

---

### Post by wojox on 2009-11-13
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

---

### Post by EvansFive on 2009-11-13
Rebooted system, went into rEFIt terminal.

Did gptsync, it said partitions were already sync'd

Did restart and selected Legacy OS icon.

Went to GRUB> prompt again

?????

---

### Post by sevenflo on 2009-11-22
I'm having the same problem on a clean install. Not sure what rEFIt is....Mac thing?

Anyway, I'm on a Dell Desktop PC. The drive I'm installing to has nothing installed on it. However, it is a hotswap hard drive connected to a Vantec SATA controller (system supports only IDE).

Any ideas?

---

### Post by linuxopjemac on 2009-11-22
rEFIt one needs to boot other operating systems on an Intel Mac.

---

### Post by jamesey on 2009-12-11
anyone find a simple solution for this?

---

### Post by linuxopjemac on 2009-12-12
[http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk](http://mac.linux.be/content/gptsync-gpt-partition-type-unknown-found-will-not-touch-disk)

---

