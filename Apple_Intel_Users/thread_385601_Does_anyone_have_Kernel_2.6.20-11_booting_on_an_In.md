---
title: "Does anyone have Kernel 2.6.20-11 booting on an Intel Mini?"
date: 2007-03-15
forum: Apple Intel Users
---

### Post by Darrena on 2007-03-15
I am running Feisty on my Intel Mac Mini but starting with kernel 2.6.20-9 it won't boot.  If I remove the splash and quiet I see that it is unable to set xfer rate on the drive and keeps trying slower speeds until it fails. 

It boots fine on 2.6.20-8, is anyone else seeing this issue?

Thanks!

---

### Post by wigglydiggly on 2007-03-15
I have the exact same problem.  Everytime there is a kernel upgrade I have to edit GRUB to auto start 2.6.20-8 because on Macbook C2Dual I have no keyboard until kernal loaded.  If anyone knows how to workaround please post.

Thanks in advance

---

### Post by rei_t_ex on 2007-03-16
Same problem here with a Macbook CoreDuo.  It looks as if it is a problem with how the new kernels treat our SATA hard drives (or controllers?).  2.6.20-9 works for for me, but all higher versions give an

```
ATA abnormal status 0x7F on port 0x20DF
.
.
.
qctimeout cmd 0x27
failed to st xfermode (err_mask=0x40)
```

Apparently, there is a bug about this on launchpad about this here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91940](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91940)

Could anyone more knowledgeable please confirm that the only thing left to do for now is to use the old kernels?

---

### Post by Darrena on 2007-03-17
It's a good sign that one of the Ubuntu Dev's confirmed the bug in the report, hopefully one of the upcoming kernel updates will fix this.

---

### Post by Darrena on 2007-03-18
It is looked like this is fixed in 2.6.20-12

---

### Post by sleeperknight on 2007-03-18
where do you find the kernel release notes?

---

### Post by rei_t_ex on 2007-03-18
Yup, the new kernel fixes it for me as well.  Thank you, developers!

---

### Post by Tribe on 2007-03-19
Hi there,

2.6.20-9 to 11 didn't boot for me in a MacBook Pro C2D and -12 does and it seems very well, now i even got the backlight thing working :)

Bye

---

### Post by vh1 on 2007-03-22
> **rei_t_ex said:**
> Yup, the new kernel fixes it for me as well.  Thank you, developers!

same deal with me. I have a macbook c2d and only 2.6.20-9 would work. 2.6.20-12 has the issue solved!

---

