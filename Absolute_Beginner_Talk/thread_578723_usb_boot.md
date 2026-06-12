---
title: "usb boot"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-10-17
Hi,
I have a usb external disk on which couple of partitions
/
/home
/mnt/data
swap

so i install linux properly but when i try to boot it from the laptop which i used to install it
i get grub error 17
i am sure the linux is installed but there is a problem with my grub, i have it installed on the usb
anyone solved this?
many thanks

---

### Post by Hospadar on 2007-10-17
I would bet that the problem is that you have grub located in the wrong place, or that you put grub on your main hard drive (which would be ok) but you are trying to boot off a different drive.  What happens when you boot off the regular internal drive?

---

### Post by LowSky on 2007-10-17
here is a list of what thos codes mean

[http://www.uruk.org/orig-grub/errors.html#stage2](http://www.uruk.org/orig-grub/errors.html#stage2)

Seems to me that your grub list is pointing to the wrong usb

---

### Post by evkefalas on 2007-10-17
thanx for the replies
i install the grub on the external usb disk
and now when i try to boot with the primary hard drive deactivated
the grub loads i select linux kernel
and then while loading it freezes

basically what i want to do is have an external bootable disk with linux that i can move to different pcs is that possible?
thanx

---

### Post by Keith_Burton on 2007-10-17
I remember one of the major Linux magazines had a how-to article on this a few months back, but can't find it now, naturally. However I did some Googling and found an IBM how-to for you: [http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw09FireBoot)

We use a "two-phase boot", when you get to that part of the article.

---

