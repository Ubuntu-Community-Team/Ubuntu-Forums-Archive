---
title: "connecting computers over lan and wlan"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-10-24
Hi

 I would like to know the best possible (and safest) way to connect 3 computers over a lan. The configuration is as follows:

My internet configuration is:
Modem <--> Router <---> Computers


**COMPUTER A** :  
Running Ubuntu fiesty
connected to router via lan (wired)

**COMPUTER B** : 
Running Ubuntu fiesty
connected to router via lan (wired)

**COMPUTER C** :
Running 'Windows Vista
connected to router wirelessly

Since I would not be needing to transfer/view files frequently , I guess it would be best if I can switch the 'sharing' on-off as required (in the best interest of security).

Thanks

---

### Post by explainer on 2007-10-24
I use samba.  I have a mix of Windows 2000 and Ubuntu 7.04 systems and virtual machines, and I can share any file tree I wish across the network.  I also found a method using smbfs to automount remote shares.  Read up on Samba and give it a try.

---

### Post by genbuntu on 2007-10-25
Ok, thanks. I'll search for Samba. I hope it will work with Vista and is secure! :)

---

