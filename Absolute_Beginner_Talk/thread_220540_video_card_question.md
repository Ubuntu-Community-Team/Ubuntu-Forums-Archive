---
title: "video card question"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by notjohn101 on 2006-07-21
as of right now i am usinbg the onboard video but in the near future i want to upgrade to an PCI graphics card (no AGP on my motherbaord) what do i need to do so i dont have any black screen

---

### Post by adam.tropics on 2006-07-21
have a look [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) and learn from the experiences of others!

---

### Post by notjohn101 on 2006-07-21
ok turns out the one i wanna install is fully supported w/ 3d and all that

---

### Post by Jagot on 2006-07-21
Oops, ignore me.

---

### Post by adam.tropics on 2006-07-21
> **Jagot said:**
> Assuming it's a fairly recent card it should just be a matter of:

```
sudo aptitude update && sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
``` 
Then reboot.

Ok, but what if, heaven forbid, he doesn't buy nvidia!

---

### Post by Jagot on 2006-07-21
> **adam.tropics said:**
> Ok, but what if, heaven forbid, he doesn't buy nvidia!

Oops, apologies, posted in the wrong topic.

---

### Post by notjohn101 on 2006-07-22
yea the one i want is ATI

ok i downloaded the first one in the list at

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

is that a driver? if it is how do i use it....because it black screens w/o a driver

---

