---
title: "Which version of libusb do I have?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by oliverb on 2006-08-19
I'm having trouble following the version numbers, I have downloaded a program that says it requires 0.1.8 and Sourceforge reports the latest is 0.1.12 but the version I see in Synaptic seems to have a whole string of version numbers.

I see the title is libusb-0.1-4

but then the version is 2:0.1.10a-22ubuntu1(dapper)

Does that mean it's 0.1.10?

---

### Post by Klaidas on 2006-08-19
As far as I understand version number, it should be 0.1.10a

---

### Post by oliverb on 2006-08-19
Thanks, I found out why the program wouldn't work, it wasn't versions, the makefiles are wrong somehow.

I was trying to get the k8055 interface software at [http://linuxk8055.free.fr/](http://linuxk8055.free.fr/)

to compile. When I issue the command manually with the option -lusb it works.

Well mostly, it's still not very helpfull as it has to run as root and I don't want to have to use sudo every time.

---

