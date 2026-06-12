---
title: "Is this guide obsolete?"
date: 2007-11-27
forum: Apple Intel Users
---

### Post by nalencer on 2007-11-27
Hi. I'm attempting to triple boot OS X, XP and Ubuntu on my Intel Mac. I've found this guide, but it says it's for Ubuntu 6.06/6.10. Can anyone tell me if this guide will work with 7.10, or what sections need to be omitted or changed? Thanks.

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

---

### Post by macaholic on 2007-11-27
I would say that it is, especially the ubuntu part, seeing as many of thes steps mentioned are unneccesary. Search around the forums and you will be sure to find some guide that is suitable for you. Also, [this]("https://wiki.ubuntu.com/MacBookPro") one is still relevant and may work for you. Just ignore the stuff about the ATI driver, unless you have an ATI card and want to install that driver :).

---

### Post by nalencer on 2007-11-27
Can you (or someone) elaborate on the use of Bootcamp as far as that guide goes? It never seems to clearly state what it wants you to do with it.

---

### Post by leogibson on 2007-11-28
im confused too, are we using bootcamp to partition here? or the terminal...in osx or ubuntu?  i dunno i may read it a few more times very carefully.  i have a macbook, and i want to know if this is better than using the main wiki : [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

---

### Post by cyberdork33 on 2007-11-28
you can use bootcamp OR the terminal method. they are both doing the same thing essentially.

---

### Post by nalencer on 2007-11-28
I used the terminal. How is Bootcamp supposed to do the trick when it only creates two partitions? I guess you then use the terminal to split one of them?

Oh, yes, I just checked the guide and its main instruction is to split the OS X partition, but also gives instructions to partition from scratch in the terminal.

I did, however, use Bootcamp to burn a Windows drivers disk. So I got that much use out of it.

---

### Post by macaholic on 2007-11-28
Well, you are supposed to make one partition with bootcamp and then the other with linux.

---

### Post by nalencer on 2007-11-28
Seems to be working this way.

---

### Post by cyberdork33 on 2007-11-28
just create a partition with bootcamp (or whatever way), then in the ubuntu live cd, delete the second partition, and choose to install to the "free space" in the installler.

---

