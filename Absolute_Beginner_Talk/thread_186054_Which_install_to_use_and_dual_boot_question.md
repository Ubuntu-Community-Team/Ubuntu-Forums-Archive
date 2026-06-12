---
title: "Which install to use and dual boot question"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by 00zero on 2006-06-01
im working at a university and i have bene given the task to setup a dell power edge server with a 64-bit xeon processor to dual boot windows and linux. My first question is since the only thing that will be run on the computer are simulations and mathmatical should i use the 32 or 64 bit version of ubuntu. Can 32-bit programs be run on 64-bit ubuntu? 

second for the dual boot i was planning on using this method because it allows for the best flexability...

[dual boot]("http://enterprise.linux.com/enterprise/05/02/16/1919205.shtml?tid=129&tid=49")

i was wondering if this is possable with ubuntu? and what the best drive format to use is?

thanks
Jonathan

---

### Post by bruenig on 2006-06-01
> im working at a university and i have bene given the task to setup a dell power edge server with a 64-bit xeon processor to dual boot windows and linux. My first question is since the only thing that will be run on the computer are simulations and mathmatical should i use the 32 or 64 bit version of ubuntu

I would recommend the 32 bit version. There is far less hassle concerning application compatability and since you aren't doing anything that really requires the power of 64 bit, I wouldn't bother. 

> Can 32-bit programs be run on 64-bit ubuntu?

They can and it is certainly much easier with Dapper than with Breezy, but there is still problems with some 32 bit apps.

> second for the dual boot i was planning on using this method because it allows for the best flexability..

That method seems fine to me but I would choose the alternate iso just to be sure because the other iso installs the Grub bootloader on the master boot record automatically whereas the alternate iso from what I understand is the old text based install which gives you the option of installing it.

---

### Post by PingunZ on 2006-06-01
You can run all the software that is in 64-bit with 32-bit, you can even run a lot more then with 64bit. So I would use x86

Dual boot, I haven't read the article on the site you referred to but ubuntu easily detect MS and makes it dual boot with grub ... 

I hope this helped you.

Grtz Pingunz

---

### Post by catlett on 2006-06-01
If you want some screen shots, my signature has 2 links to dual boot how tos. 1 is for dapper and one is for breezy. The breezy one will be similar to the dapper text install and of course the dapper one is screen shots of the live cd dapper install. Just for some graphical reference.

---

### Post by Sef on 2006-06-01
Have you checked out [Herman's dual boot site?]("http://users.bigpond.net.au/hermanzone/")  It has pics included of how to dual boot.

---

