---
title: "why wont my 686-smp kernel work right?"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by jrjr on 2006-08-26
.

---

### Post by tseliot on 2006-08-26
I can only suggest you to file a bug (for the SMP kernel) on launchpad. The kernel team should be able to tell you whether it depends on the kernel or on some problem with the driver.

Here is the link to the page about the kernels:
[https://launchpad.net/products/linux](https://launchpad.net/products/linux)

---

### Post by az on 2006-08-26
Did you install linux-686 or only linux-image-686?

The linux-686 package also installs the needed restricted-modules package.   Maybe that is your problem?

---

### Post by jrjr on 2006-08-26
.

---

### Post by kaamos on 2006-08-26
> I wrote what I did already

Yea, but you're not particulary clear on what package you installed. linux-686 pulls in a number of packages, linux-image-686 only the kernel package and linux-image-2.6.15-26-686 is a single package (that the other packages install).

---

### Post by jrjr on 2006-08-26
.

---

