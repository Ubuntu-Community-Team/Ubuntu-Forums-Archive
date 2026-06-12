---
title: "asus 1015pn won't wake from suspend"
date: 2012-08-03
forum: Asus Ubuntu Support (CLOSED)
---

### Post by 510carl on 2012-08-03
I am using ubuntu 11.10 on asus 1015pn. It used to wake from suspend, but now it wont. I've tried some solutions that I googled, but I haven't tried the more complex ones as they are beyond my ability. I have used ubuntu for 5 yrs and don't want try an other distro, or go back to window$.

---

### Post by 510carl on 2012-08-03
It looks the problem is that I installed the latest nvidea driver from their site. How do I revert back to older driver?

---

### Post by 510carl on 2012-08-04
Can anyone help me?

---

### Post by Nutria on 2012-08-04
> **510carl said:**
> It looks the problem is that I installed the latest nvidea driver from their site.

Who's site?  Nvidia's or Ubuntu's?

> How do I revert back to older driver?

Depends on the answer to my first question.

---

### Post by 510carl on 2012-08-05
> **Nutria said:**
> Who's site?  Nvidia's or Ubuntu's?



Depends on the answer to my first question.

Thank you for the reply. I think it was the nvidia site. The version that I installed is: 302.17, which is a beta version. I need to un-install it and install the current certified version: 295.59, as I feel that the driver is causing my wake from suspend/hibernate issue. When I tried the sudo install thing, it said that I already had the current version.

---

### Post by Nutria on 2012-08-05
> **510carl said:**
> Thank you for the reply. I think it was the nvidia site. The version that I installed is: 302.17, which is a beta version. I need to un-install it and install the current certified version: 295.59, as I feel that the driver is causing my wake from suspend/hibernate issue. When I tried the sudo install thing, it said that I already had the current version.

Google "linux nvidia uninstall".  First, though, install the nouveau package.

---

