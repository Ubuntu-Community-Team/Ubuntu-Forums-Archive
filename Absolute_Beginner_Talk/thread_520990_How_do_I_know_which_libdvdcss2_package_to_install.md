---
title: "How do I know which libdvdcss2 package to install?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by hul on 2007-08-08
I have found the libdvdcss2 packages [here]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/"), but dang if I know which one to use.  I know I'm not AMD.  I might be i386?  Or powerPC?  I feel dumb for not knowing this.  I'm using Feisty 7.04.

Thank you!

EDIT: On looking up i386 on Wikipedia, I am pretty sure that's not what I am--my computer is brand-new.

---

### Post by Bachstelze on 2007-08-08
Don't you remmeber which CD yo uused to install your Ubuntu ? Anyway, type *uname -m* in a terminal, it will tell you.

---

### Post by RomeReactor on 2007-08-08
Hi. Enter the following in the terminal:
```
uname -m
```
it will tell you what architecture you're running--i386 (32-bit) or AMD64 (64-bit).

---

### Post by hul on 2007-08-08
It says i686--so should I use the i386?  Also, which build do I use?  There are a lot.

---

### Post by overdrank on 2007-08-08
> **hul said:**
> I have found the libdvdcss2 packages [here]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/"), but dang if I know which one to use.  I know I'm not AMD.  I might be i386?  Or powerPC?  I feel dumb for not knowing this.  I'm using Feisty 7.04.

Thank you!

EDIT: On looking up i386 on Wikipedia, I am pretty sure that's not what I am--my computer is brand-new.

Hi or you could just use this "how to"
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Good Luck! 

P.S. Thanks HymnToLife I was trying to remember that command. ;)

---

### Post by Dr Small on 2007-08-08
> **overdrank said:**
> Hi or you could just use this "how to"
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Good Luck! 

P.S. Thanks HymnToLife I was trying to remember that command. ;)
I have them on record in my facl (frequently accessed command list)

> 
hostname = drsmall
uname -m = i686
uname -r = 2.6.15-27-386
uname -s = Linux
uname -v = #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006


---

### Post by RomeReactor on 2007-08-08
> **hul said:**
> It says i686--so should I use the i386?  Also, which build do I use?  There are a lot.

You're using 32-bit. You should install the [i386 version of libdvdcss2]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_i386.deb"). If you were using Ubuntu 64-bit, you would have gotten **x86_64**.

---

### Post by hul on 2007-08-08
I got it installed!  Thank you for your help!

---

