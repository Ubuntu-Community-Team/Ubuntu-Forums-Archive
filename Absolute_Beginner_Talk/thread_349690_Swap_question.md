---
title: "Swap question"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by rojyne on 2007-01-30
Hello. I am Ubuntu Edgy user. I wish to install edubuntu for my daughter . Can I use the same swap partition of the Ubuntu for Edubuntu?

Second question; 
I am 512 mb Ram user and  and 3.0Ghz Intel processor. I sized swap as 256mb . If I increase the swap size to 512mb, will I get performance increase ? 

Thanks in advance.

---

### Post by taurus on 2007-01-30
Yes, you can share the same swap partition between Ubuntu & Edubuntu.  

Depends on what you have open on your machine, 512MB of RAM should be enough but if you can increase your swap space to 512MB, then it would be better.  You probably won't notice a whole lot of improvement in performance though.

---

### Post by rojyne on 2007-01-30
> **taurus said:**
> Yes, you can share the same swap partition between Ubuntu & Edubuntu.  

Depends on what you have open on your machine, 512MB of RAM should be enough but if you can increase your swap space to 512MB, then it would be better.  You probably won't notice a whole lot of improvement in performance though.

Thanks @Taurus. Can I use same root partition for Edubuntu,too?

---

### Post by taurus on 2007-01-30
You mean root partition as in /!  If that's the case, it's not a good idea because stuff would get conflicted.  But if you have a /boot, then you can share it as long as the kernels don't have the same name in them.

---

