---
title: "Kernel Source code"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2006-02-22
Is there any automated way of installing kernel sources (like using apt-get).  Or should I download the kernel source code and copy it in /usr/src directory.

Thanks!!
vijay

---

### Post by heimo on 2006-02-22
Install one of the linux-source-* packages. It'll place source package in /usr/src directory, but you still need to unpack it using something like

```
cd /usr/src
sudo tar xjvf linux-source-2.6.12.tar.bz2

```

---

