---
title: "[SOLVED] no device entry for ath0 on Macbook Pro 2,1"
date: 2008-10-04
forum: Apple Hardware Users
---

### Post by dsmoot on 2008-10-04
I upgraded to a larger drive and had to reinstall everything.  Last time everything "just worked" but now I have a problem.  I have no /dev/ath0 entry.

Could someone please give me the output of ls -al /dev/ath0?  Thank you,
David

---

### Post by dsmoot on 2008-10-04
Nevermind... problem seemed to fix itself after a sudo rmmod ath_pci and then sudo modprobe ath_pci autocreate=ap and a reboot.

David

---

