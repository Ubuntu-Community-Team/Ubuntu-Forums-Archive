---
title: "Is Ubuntu the right distro for me?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by krolben on 2007-04-22
Hi all

I'm currently trying to install Ubuntu to my home server, but have many problems getting it up and running. I've therefore started to wonder if maybe it's not the best distro for my needs.

My system is:
Via Epia ME 6000 LVDS mini-ITX motherboard
1 GB internal HDD (flash card connected to IDE)
320 GB external HDD

The usage of the server will be file/music sharing, personal web server and some time in the future a mail server.
I know that Ubuntu can handle these things for me very well, and I'd love to use the server version. It seems however that Ubuntu has issues running on the mini-itx motherboard.

Is there another distro that's better than Ubuntu Server? Preferably one that can be running only on the 1GB disk. I'm still kinda of linux n00b, so a distro that has something similar to apt-get would be nice. No graphical interface is needed since I'll be connecting to the server through SSH.

---

### Post by Seisen on 2007-04-22
What kind of issues are you having?

---

### Post by krolben on 2007-04-22
> **Seisen said:**
> What kind of issues are you having?

When the server version is installed I get this error on boot:
Unknown interupt or fault at EIP 00010046 00000060 c01bc24f

I've searched my way to an answer saying that the Ubuntu Kernel is compiled in a way that does not allow it to work on the mini-itx board ([https://launchpad.net/ubuntu/+bug/71594)](https://launchpad.net/ubuntu/+bug/71594)).

I'm currently trying to install the Alternate version of Feisty instead. We'll have to see how that ends up. Otherwise I've been thinking of trying Debian 4 (but would definitely prefer Ubuntu Server!).

---

### Post by lamalex on 2007-04-22
doesn't EIP deal with memory? you might want to do a mem check and make sure your system is ok!

---

### Post by krolben on 2007-04-22
> **Iamalex said:**
> doesn't EIP deal with memory? you might want to do a mem check and make sure your system is ok!

I thought so too, but I made a mem-test yestarday, and it didn't find any errors. I've previously had Ubunto Edgy Desktop installed on the system with no issues.

---

### Post by Swab on 2007-04-22
There was a distro made especially for those Epia Mini ITX boards... I can't remember what it was called and can't find any reference to it on google...

---

### Post by krolben on 2007-04-22
> **Swab said:**
> There was a distro made especially for those Epia Mini ITX boards... I can't remember what it was called and can't find any reference to it on google...

Interesting. I'll see if I can find more info on that! Thanks

---

### Post by blackened on 2007-04-22
> **Swab said:**
> There was a distro made especially for those Epia Mini ITX boards... I can't remember what it was called and can't find any reference to it on google...

IIRC [Damn Small Linux]("http://www.damnsmalllinux.org") is largely aimed at the mini-itx crowd. In fact I'm pretty sure they have an install tailored for solid state media that reduces disk-writes by the OS. Look around their websites and forums for information on installing with the "frugal" option.

---

### Post by Swab on 2007-04-22
Got it.. [http://www.epios.net/](http://www.epios.net/)

edit: hmmm, not much going on there!

---

### Post by askreet on 2007-04-22
Installing a source-based distro on a computer with limited resources is going to be slow.  Also, consider that portage itself consumes 700Mb+... You'll have to put /var/ on your external disk.

---

### Post by krolben on 2007-04-22
> **askreet said:**
> Installing a source-based distro on a computer with limited resources is going to be slow.  Also, consider that portage itself consumes 700Mb+... You'll have to put /var/ on your external disk.

Yep! The idea is to put /home and /var on the external disk.
I'll have a look at the links and see what works best for me. Thanks a lot!

---

