---
title: "DVDs"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-05-19
I bet that this has been asked a few milion times, but how does one go about watching copyright protected DVDs with Totem? Or any other movie player in Ubuntu? They all say I haven't got rights and stuff. I was wondering if I had to download a decoder or something of the like.

---

### Post by DerArzt on 2007-05-19
Don't know how well this works, but I imagine it does.
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)
good luck

---

### Post by DerArzt on 2007-05-19
it seems libdvdcss2 is the only package necessary for it, sop id try that first, and if it doesnt revert to the guide in my previous post

---

### Post by teknosexual on 2007-05-19
The easiest way (in my opinion) is to use [Automatix]("http://getautomatix.com/"). You can get other good things with Automatix as well, but using it to configure Ubuntu for dealing with a DVD's CSS.

---

### Post by shuttleworthwannabe on 2007-05-19
Just to add here, I had to also install **regionset** (in my case I am in Zone 2) using synaptic.

After installing it, in terminal type sudo regionset, and follow the instructions, and DVD will play; otherwise you will get errors even if you have libdvdcss2 installed.

HTH,
SWB

---

### Post by hyper_ch on 2007-05-19
The easiest way may not be the best one... you need to install the according libraries

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by tbasherizer on 2007-05-23
Thanks, I just watched Monty PYthon and the Holy Grail.

---

### Post by Ek0nomik on 2007-05-23
> **tbasherizer said:**
> Thanks, I just watched Monty PYthon and the Holy Grail.

Excellent.  :)  I hope you didn't use Automatix.  ;)

---

