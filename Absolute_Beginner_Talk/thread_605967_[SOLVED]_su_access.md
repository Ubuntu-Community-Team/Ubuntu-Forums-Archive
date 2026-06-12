---
title: "[SOLVED] su access"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by robert scott on 2007-11-07
Hello ...

First off thanks for helping out !!

I have recently installed Ubuntu 6.10 ( server disc not installed ) 
I can not login as su in terminal window ...
Authentication failure on entering password .... ( user name is member of Admin group ) 

Any help would be greatly appreciated !! 

Thanks 
Robert Scott

---

### Post by aysiu on 2007-11-07
```
sudo -i
``` instead of ```
su
``` should work.

More details here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by poudin on 2007-11-07
just wondering if you have established a root password...if not

sudo passwd....enter password of non-root account and then set a 'root' password. I don't believe it to be set until you have done this step.

---

### Post by aysiu on 2007-11-07
> **poudin said:**
> just wondering if you have established a root password...if not

sudo passwd....enter password of non-root account and then set a 'root' password. I don't believe it to be set until you have done this step.
It's not necessary to set a root password.

---

### Post by markharding557 on 2007-11-07
> **robert scott said:**
> Hello ...

First off thanks for helping out !!

I have recently installed Ubuntu 6.10 ( server disc not installed ) 
I can not login as su in terminal window ...
Authentication failure on entering password .... ( user name is member of Admin group ) 

Any help would be greatly appreciated !! 

Thanks 
Robert Scott

open a terminal do sudo -i this will open a root terminal for a limited time or you can enable the root account which ubuntu don't recomend command is"sudo passwd root" it will ask to enter a password

---

### Post by robert scott on 2007-11-07
Thanks all !!

Got it !

---

