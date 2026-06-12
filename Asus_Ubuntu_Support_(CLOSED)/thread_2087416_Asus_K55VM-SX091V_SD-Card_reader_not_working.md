---
title: "Asus K55VM-SX091V SD-Card reader not working"
date: 2012-11-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by BongoRongo on 2012-11-23
Hello

The card reader in the Asus is not working out of the box.
Works ok in Windows.

Generic SD-card reader is present in Ubuntu's disk management.
But it will not mount the cards i insert.

---

### Post by zezadas on 2012-11-27
> **BongoRongo said:**
> Hello

The card reader in the Asus is not working out of the box.
Works ok in Windows.

Generic SD-card reader is present in Ubuntu's disk management.
But it will not mount the cards i insert.


enable card reader on kernel(i would update new kernel for fn fix and much more)
and install this [http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb](http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb)

---

### Post by BongoRongo on 2012-11-27
> **zezadas said:**
> enable card reader on kernel(i would update new kernel for fn fix and much more)
and install this [http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb](http://planet76.com/drivers/realtek/rts-bpp-dkms_1.1_all.deb)

Driver worked fine. Thanks!
Not sure how to update kernel.
I'm running 3.5.0-18-generic. (uname -r)

---

