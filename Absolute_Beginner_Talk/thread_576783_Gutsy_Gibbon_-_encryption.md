---
title: "Gutsy Gibbon - encryption??"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by damatta on 2007-10-15
Hiya,

I have gone through this forum and gudies but still have not found step-by-step how to encrypt from the installation.
I have windows on sda1 and sda2; therefore I'm forced to use the manual scheme. So, how should I partition the 35 GB left so that I have an encrypted file system?

Thanks in advance! :)

---

### Post by LowSky on 2007-10-15
on the live CD  under manual partition and set up a root and swap partitions for ubuntu

Root's mount point should be this```
/
``` use how much of you HD you want make the file system ext3

swap doesn't need a mount point and only needs to be abould 512Mb of space.

---

### Post by damatta on 2007-10-15
Is it valid for Kubuntu? Because I'm installing in text mode and I was confused on how to encrypt my HD using AES.
Thanks for your reply

---

### Post by damatta on 2007-10-16
I set up a logical partition of about 30GB as "Encrypted volume" and 1GB for SWAP and 4MB for "/".
Is it the right way to go? I still have not found the most secure way of encrypting the whole thing!
Thanks

---

### Post by bodhi.zazen on 2007-10-16
Use the alternate CD : [http://www.phoronix.com/scan.php?page=article&item=873&num=1](http://www.phoronix.com/scan.php?page=article&item=873&num=1)

---

### Post by damatta on 2007-10-16
The way I installed it using the Alternate CD I was not prompted for a password at boot but at the login screen only. I supposed the installer would support encrypting everything, including "/", SWAP etc...
I hope having a primary partition as encrypted volume and root + swap as logical is enough.

once more: thanks for the help

---

