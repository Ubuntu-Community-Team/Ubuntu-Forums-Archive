---
title: "obtaining/installing deb packages"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by dfeiling on 2006-09-08
I have had problems installing Mythtv from the "published packages" available from Ubutnu.  In researching the problem it is due to an incompability of the packages installed by Synaptic with MySql 5.0.( use of a word reserved in 5.0 )
In reading the forums I cannot just downgrade MySql to 4.0 due to dependicies.  A member of the user community has published two .deb packages to solve the reserved word problem.
[http://atdot.ca/mythtv-backend_0.18.1-5ubuntu3_i386.deb](http://atdot.ca/mythtv-backend_0.18.1-5ubuntu3_i386.deb)
[http://atdot.ca/libmyth-0.18.1c2a_0....untu3_i386.deb](http://atdot.ca/libmyth-0.18.1c2a_0....untu3_i386.deb)

My problem is I am new to Ubuntu previously using SUSE and rpm to install.  And even after looking at apt, dpkg etc I cannot figure out how to proceed.

Can anyone tell me How do I 

1.  get the above two packages, tried wget can'a seem to make that work

2. Once packages obtained, how would I install them.

---

### Post by chajuram on 2006-09-08
Hi,

Get the files however you can and save it in some place. Then do 

sudo dpkg -i pkgname.deb

CHajuram

---

