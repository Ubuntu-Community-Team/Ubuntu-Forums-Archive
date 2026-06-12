---
title: "[SOLVED] Questions About Bootcamp and Triple Booting"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by acelin on 2008-06-09
I am about to buy an iMac, and I want to triple boot with OS X, Vista, and Ubuntu. 

Am I correct in that I can just partition using Bootcamp, install Windows, then install Ubuntu into the third partition making sure that Grub is installed as only the MBR of that particular partition, much like you would an External Hard Drive?

---

### Post by cyberdork33 on 2008-06-09
There is only one MBR on your entire hard drive... You will want to install Grub to the Ubuntu root partition. Make sure to checkout some of the installation guides available in the community documentation:

This is for Macbook Pro, but the bse install process is the same for every Mac:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Some iMac documentation here:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by acelin on 2008-06-10
> **cyberdork33 said:**
> There is only one MBR on your entire hard drive... You will want to install Grub to the Ubuntu root partition. Make sure to checkout some of the installation guides available in the community documentation:

This is for Macbook Pro, but the bse install process is the same for every Mac:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Some iMac documentation here:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

Cool. I figured that is how it would work. Thanks for the confirmation.

---

### Post by jsoreno on 2008-06-10
hmm what do u mean by triple booting? hmmm still curious coz have not yet encounter that ever

---

### Post by acelin on 2008-06-10
> **jsoreno said:**
> hmm what do u mean by triple booting? hmmm still curious coz have not yet encounter that ever

OS X
Vista
Ubuntu

---

