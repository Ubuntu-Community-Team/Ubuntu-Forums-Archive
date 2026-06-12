---
title: "compile kernel"
date: 2005-03-19
forum: Apple PPC Users
---

### Post by cvalstad on 2005-03-19
whats the best way to easily compile the kernel in hoary ppc, and what files would be needed. i need to bring them manually since i dont have a internet connection.

---

### Post by az on 2005-03-19
build-essential, linux-source should all be on your cd already.

I think kernel package is there, too.  That is the easiest way to go.


cd /usr/src
tar xvjf linux-source*
cd linux-source*
cp /boot/config(whateverversionyouhave) .config
make-kpkg --revision=1 --append-to-version=mykernel kernel_image kernel_headers


then 
cd ..
dpkg -i linux-image*

---

