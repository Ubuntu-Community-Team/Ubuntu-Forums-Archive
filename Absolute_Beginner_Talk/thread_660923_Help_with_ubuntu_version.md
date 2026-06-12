---
title: "Help with ubuntu version"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by ksujason on 2008-01-07
I just built a new computer with an AMD64 processor over the weekend. I installed ubuntu from a live CD that I had. 
I was wondering if there was a way to check and see if I installed the 32 or 64 bit versions? I can't remenber what I selected when I made the live CD.
I am having so many problems trying to get Flash installed, if I do have the 64 bit version I will probably put on the 32 bit.

Thanks

---

### Post by (((X))) on 2008-01-07
if you had x84, it would not even run

---

### Post by ksujason on 2008-01-07
Ok thanks, so I must have the AMD 64 bit version then.

---

### Post by p_quarles on 2008-01-07
> **(((X))) said:**
> if you had x84, it would not even run
Huh? That's certainly not true. 

> **ksujason said:**
> Ok thanks, so I must have the AMD 64 bit version then.
Simple way to check your architecture:
```
dpkg --print-architecture
```

---

### Post by ksujason on 2008-01-07
> **p_quarles said:**
> Huh? That's certainly not true. 


Simple way to check your architecture:
```
dpkg --print-architecture
```

Thanks, I will try this when I get home tonight and check my architecture.

---

### Post by SOULRiDER on 2008-01-07
Or you can just type
```
arch
``` in a terminal.

---

### Post by p_quarles on 2008-01-07
> **SOULRiDER said:**
> Or you can just type
```
arch
``` in a terminal.
I'm guessing that's an Arch Linux tool? Doesn't work in Ubuntu. I believe there is a simpler command to get the architecture, but I can never remember it.

---

### Post by (((X))) on 2008-01-07
.but, why are there 2 flavors of ubuntu, one is i368, another x64..?

---

### Post by PetePete on 2008-01-07
> **(((X))) said:**
> .but, why are there 2 flavors of ubuntu, one is i368, another x64..?

because x64 has library's which are designed to run on 64 bit machines... basically ubuntu is tweaked to run faster on 64bit and utilise the extra 32bits !

---

### Post by John.Michael.Kane on 2008-01-07
> **p_quarles said:**
> I'm guessing that's an Arch Linux tool? Doesn't work in Ubuntu. I believe there is a simpler command to get the architecture, but I can never remember it.

```
 uname -m
```

And if the OP is running a 64bit ubuntu will return the below output
```
x86_64
```

> **ksujason said:**
> I just built a new computer with an AMD64 processor over the weekend. I installed ubuntu from a live CD that I had. 
I was wondering if there was a way to check and see if I installed the 32 or 64 bit versions? I can't remenber what I selected when I made the live CD.
I am having so many problems trying to get Flash installed, if I do have the 64 bit version I will probably put on the 32 bit.

Thanks
What issues are you having with flash?

There is currently a known md5 mismatch issue regarding installing flash from the repo. more info is listed here [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) along with the thread starter workaround. Another known workaround is listed here [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) as well.

---

### Post by ksujason on 2008-01-07
> **John.Michael.Kane said:**
> ```
 uname -m
```

And if the OP is running a 64bit ubuntu will return the below output
```
x86_64
```


What issues are you having with flash?

There is currently a known md5 mismatch issue regarding installing flash from the repo. more info is listed here [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669) along with the thread starter workaround. Another known workaround is listed here [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) as well.

When I run the script I found to install flash, I get the following.

Selecting previously deselected package nspluginwrapper.
(Reading database ... 88046 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_0.9.91.6_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
nspluginwrapper depends on ia32-libs (>= 1.6); however:
Package ia32-libs is not installed.

I guess I need to find out for sure if I installed the 32 or 64 bit version.

---

