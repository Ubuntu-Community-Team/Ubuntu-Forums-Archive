---
title: "APT Errors."
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by Umbra on 2005-07-10
Im always getting dependencies errors when using apt-get command for every single package i have tried to install. I updated my sources list with the info provided in the obuntuguide.org and everything seems to be ok.  

Im new to linux and dont know what else to do. Im using kubuntu in amd64 distribution.

---

### Post by poofyhairguy on 2005-07-11
[QUOTE=Umbra]Im always getting dependencies errors when using apt-get command for every single package i have tried to install. I updated my sources list with the info provided in the obuntuguide.org and everything seems to be ok.  

Im new to linux and dont know what else to do. Im using kubuntu in amd64 distribution.[/QUOTE]

The 64 bit version is made for Linux pros, and lacks many packages like Java, codecs, and so forth. I suggest installing the 32 bit Kubuntu if you need that.

---

### Post by Umbra on 2005-07-11
You mean that if im new to linux i shouldnt work with this distribution?
Well, i just download the most adecuate to my hardware, didnt know it was made por pros.

---

### Post by poofyhairguy on 2005-07-11
[QUOTE=Umbra]You mean that if im new to linux i shouldnt work with this distribution?[/QUOTE]

Its up to you. If you need Media Codecs, Flash in the browser, or Java, you have to do this in the 64 bit version:

[https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29](https://wiki.ubuntu.com/DebootstrapChroot?highlight=%28chroot%29)

In the 32 bit version you just do the easier stuff the guide says. Its up to you I guess.

>  i just download the most adecuate to my hardware, didnt know it was made por pros.

This 64 bit stuff is new. There isn't even a true 64 bit Windows yet...it will get easier someday. Till then...try the 32 bit version. I've heard it works great on AMD CPUs (all of mine are Intel....)

---

### Post by Umbra on 2005-07-11
> [https://wiki.ubuntu.com/Debootstrap...ht=%28chroot%29](https://wiki.ubuntu.com/Debootstrap...ht=%28chroot%29)

What is that for?

---

### Post by poofyhairguy on 2005-07-11
[QUOTE=Umbra]What is that for?[/QUOTE]

That allows you to run the 32 bit version of Ubuntu within the 64 bit version. It really only avoids the problem from the user's end.

---

