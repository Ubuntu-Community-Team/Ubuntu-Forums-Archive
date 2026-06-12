---
title: "What is happening with Backports? No Java? Mozilla Broken?"
date: 2005-07-22
forum: Bug Reports / Support
---

### Post by sebgate20 on 2005-07-22
I have been trying to install some bits and bobs from Backports today and I was shocked to see that the sun-j2re1.5 package is missing and mozilla is broken.

What is happening? Are these bugs known?

Seb

---

### Post by foxy123 on 2005-07-22
I guess something is wrong. I tried to install amarok with Synaptic and can see only 1.2.3 while 1.2.4 is in the repository. Hopefully it will be fixed soon....

---

### Post by jdong on 2005-07-22
Thanks for letting me know.

The /var filesystem on the master system is full... I'll let Ryan know, and we hope to have this sorted out soon!

---

### Post by jdong on 2005-07-22
Fixed. The next hourly sync will pull in the good packages.gz files, and we'll be all set again :)

---

### Post by sebgate20 on 2005-07-22
Wonder when that is in GMT? Thanks jdong!

---

### Post by foxy123 on 2005-07-22
it works fine now! thanks a lot, jdong!

---

### Post by sebgate20 on 2005-07-22
[QUOTE=foxy123]it works fine now! thanks a lot, jdong![/QUOTE]
 It ain't for me. What mirror are you using? ftp2.caliu.info is mine.

Seb

---

### Post by jdong on 2005-07-23
caliu has much slower sync cycles. Mirrormax syncs with me hourly, while caliu sometimes takes a few days per sync.

---

