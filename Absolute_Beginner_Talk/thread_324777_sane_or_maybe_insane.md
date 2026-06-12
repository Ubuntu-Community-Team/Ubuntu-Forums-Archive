---
title: "sane or maybe insane"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by squrl on 2006-12-24
Would someone please tell me what package this is looking for?  


squrl@Robby:~$ sudo apt-get install /home/squrl/sane-files/sane-frontends-1.0.14.tar.gz
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 
squrl@Robby:~$ 

Or what I should be doing to install sane set up

Thanks

---

### Post by AndyCooll on 2006-12-24
Are you trying to install a package you've downloaded? The command path you seem to be typing is to a zipped file.

You are likely to already have Xsane (Applications > Graphics > Xsane image scanner) installed as part of the default install anyway.

Otherwise you can install those via Synaptic or type into a command line:
```
sudo aptitude install xsane
```

:cool:

---

### Post by squrl on 2006-12-24
Trying to get a scanner working. Trying to follow the directions at the sane site. 
It really doesn't make any  difference now. I bought a package called vuescan. Works good. 
It really isn't any surprise why microsoft has done so well in the marketplace.

---

### Post by AndyCooll on 2006-12-24
Hmmm ...can't say I've ever had a problem with my scanner. Works out-of-the-box with Xsane. Had more problems installing damn drivers and stuff to get it to work when I was using XP.

And no it isn't a surprise why M$ have done so well in the marketplace ... they have you buying additional software you really shouldn't need to purchase.

:cool:

---

### Post by logos34 on 2006-12-25
if you really want it there is a deb package in the universe repo...same exact version.

$ sudo apt-get install sane

---

