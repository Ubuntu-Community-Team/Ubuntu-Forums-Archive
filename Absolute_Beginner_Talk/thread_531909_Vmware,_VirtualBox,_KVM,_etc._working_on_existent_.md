---
title: "Vmware, VirtualBox, KVM, etc. working on existent partition"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by slamdunk on 2007-08-22
Hi,

Can you suggest me one of multiples "virtualization software" and how to use it to run an existent partition of Vista?

Thanks,
Julio

---

### Post by tzulberti on 2007-08-22
None of the virtualization software allows you to work in a normal partition. Nevertheless, I haver read that VmWare has a program that from a partition with Windows, creates the necesarie files for a new virtual machine.

---

### Post by forestpixie on 2007-08-22
yea it's this

[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

I used it to make a virtual copy of my win install - it worked ok for what I needed at the time.
But be aware that it might take a bit of space - unless I set it up wrong. I had a 2Gb Win2k installation and the resulting virtual machine was 4Gb. So if it does double -Vista is a good deal larger than Win2K

---

### Post by slamdunk on 2007-08-22
thanks for replies,

but I don't understand exactly what vmware-converter does: it permits to use directly a phisical partition or make a kind of "copy" of it (and so I would have a 2 times same thing)?

Thanks,
Julio

---

### Post by forestpixie on 2007-08-22
> and so I would have a 2 times same thing

basically yes - there are other ways to do it - but you'd need to search the forums or google 

it all depends on what you're trying to achieve

---

### Post by slamdunk on 2007-08-22
I bought a Dell XPS M1330. Dell doesn't sell it with Ubuntu preinstalled only, and so I found Vista preinstalled. Actually it's completely unuseful for me, but in future, it could useful to run software not present in Ubuntu, always running Vista in Ubuntu. I cannot delete that partition for warranty clauses and I don't want throw away other hd-space making a "virtual partition" and re-install it, and so I would like recycle existent vista-partition.

Julio

---

### Post by sawjew on 2007-08-22
Actually you can use a physical partition with vmware server, I have done so in the past.  I had a dual boot Windows XP/Ubuntu system and I set up vmware server to access the physical Windows XP partition.  I could then work on XP in vmware or by booting into it and all my work was available in either setup.

However it does have a few problems.  To use the physical partition you have to set up another hardware profile in XP.  The problem is that when you boot into the new profile you have to reactivate Windows and again when you boot back into the other profile.  If you have an older version of Windows like Windows 2000 this would probably work quite well but it's not very successful with XP unless you have the corporate edition which does not require activation.

If you want to give it a go use this howto [http://www.motin.eu/www/mirror/physvmware/]("http://www.motin.eu/www/mirror/physvmware/")
There are plenty of other tutorials available too, just google it.

Good luck and have fun.

---

