---
title: "Dual-Core Support"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by slvrmoontiger on 2006-09-24
Hello,

I have been considering installing Ubuntu, however there are a couple of things I haven't been able to find.  I wanted to find out if Ubuntu supports Dual-Core.  Specifically, I have a AMD 939 Socket X2 4400+ processor.

I used to be really big on linux and have worked with Debian, Mandrake (now Mandriva), and Red Hat distro's primarily.  I got out of the linux community for a while and looking to get back in.  Ubuntu looks like an awesome distro but I want something that will use the power of the processor I have.

Thanks,
Albert

---

### Post by madmetal on 2006-09-24
you need to install 686-smp kernel..

---

### Post by bodhi.zazen on 2006-09-24
Yes, install the smp kernel.

---

### Post by reacocard on 2006-09-24
> you need to install 686-smp kernel..
actually, since its an athlon processor, you want the k7-smp kernel.

Note that this confusion about kernels will be fixed in the next release (edgy eft) which will have a kernel that supports multiple cores automatically.

---

### Post by Antman on 2006-09-24
> **reacocard said:**
> actually, since its an athlon processor, you want the k7-smp kernel.

Note that this confusion about kernels will be fixed in the next release (edgy eft) which will have a kernel that supports multiple cores automatically.

Nice..... \\:D/

---

### Post by slvrmoontiger on 2006-09-24
> **reacocard said:**
> actually, since its an athlon processor, you want the k7-smp kernel.

Note that this confusion about kernels will be fixed in the next release (edgy eft) which will have a kernel that supports multiple cores automatically.

Thanks for the help.  Wow that was really quick.  Ok here's the catch.  Is there a k7-smp with 64-bit kernel too?  I started poking around in the 64-bit forums and it looks intimidating to work with 64-bit.  Can I get dual-core without 64-bit or is it all or none?

Thanks,
Albert

---

### Post by madmetal on 2006-09-24
i think 64bit or 32bit depends on the ubuntu version you use..
if you install x86 dapper with k7-smp kernel you got a kernel improved for amd athlon cpu and supports dual core...
if you install amd64 dapper with k7-smp kernel you got the same but in 64bits..

---

### Post by madmetal on 2006-09-24
> **reacocard said:**
> Note that this confusion about kernels will be fixed in the next release (edgy eft) which will have a kernel that supports multiple cores automatically.

i think this is great!
wouldn't it be better to have a choise during installation?
i mean ok when things are getting simple and easy but power and stability is also needed...

---

### Post by reacocard on 2006-09-24
> **madmetal said:**
> i think this is great!
wouldn't it be better to have a choise during installation?
i mean ok when things are getting simple and easy but power and stability is also needed...

There isn't room on the cd for multiple kernels, so only the most basic (i.e. most likely to work for everyone) kernel is supplied.

---

### Post by madmetal on 2006-09-24
yes, i forgot about space... :-$ 
:-({|=

---

