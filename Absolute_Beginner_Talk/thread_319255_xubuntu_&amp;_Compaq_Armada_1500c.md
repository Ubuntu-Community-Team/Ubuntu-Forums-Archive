---
title: "xubuntu &amp; Compaq Armada 1500c"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Elhoir on 2006-12-15
Hello all 

As many other people in here I'm a newbie on linux and I have an old computer that I would like to use with linux.
The computer is an old compaq armada 1500c, I have tried to install xubuntu on it but I've got a problem right after starting the install process which is... the windows are too big for the screen resolution!! 
I think xubuntu doesn't well recognize the video card which is the C&T69000 and I don't know where to look for. Digging on the net I found this: [http://ieee.uow.edu.au/~daniel/compaq/compaq_armada_1500c/](http://ieee.uow.edu.au/~daniel/compaq/compaq_armada_1500c/)
but sounds like greek to me and maybe a little bit too outdated.

Can anyone give me some advice on how to install linux on this pc?

Thanks

---

### Post by John.Michael.Kane on 2006-12-15
The display on that machine supports 800 x 600 resolution. when booting the cd for the frist time you should be able to press F4 and select the proper resolution.



Looking over the specs of the machine  Xorg has the support for this chip so i'm not sure why your having the issue you say. it should be fully supported with out issue.

---

### Post by Egils on 2006-12-25
I have a Compaq Armada 1500c with Xubuntu installed on it. I ended up using the Alternate Install CD (which allowed me to do the install without booting into the live system first), and from memory it didn't give me any problems with screen resolution afterwards. If you don't have any success changing the screen resolution for the normal install CD it might be worth giving the Alternate CD a try.

And I don't know if you have additional memory installed, but the XFCE environment is a little slow with the stock 32MB of RAM. After you finish the install it might be worth installing Fluxbox (very easy via the Synaptic package manager) and giving this a go as well. It takes a little bit of getting used to but the gains in speed make it worthwhile.

---

