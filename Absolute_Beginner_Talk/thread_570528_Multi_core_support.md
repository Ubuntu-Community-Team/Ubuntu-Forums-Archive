---
title: "Multi core support"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-08
i have a quad core Q6600 but i have felt that Ubuntu is slow..............i also run vista on my comp and it is EXTREMELY fast.......is there some thing wrong?? considering ubuntu is supposed to be faster, isnt it??

---

### Post by skymera on 2007-10-08
yes it is. hmm .

what seems slow?

application?
general?
boot?

---

### Post by nest on 2007-10-08
with no more information that "my pc is slow". i just could think that you dont have the drivers of your video card?

---

### Post by wheredidrealitygo on 2007-10-08
I had this same problem.

I'm also running a q6600 and my problem was that I was running the wrong kernel (an i386 kernel, which didn't have SMP support, so it only supported one core.)

post the output of

```
uname -a
```

please?

mine appears as such: 
```
Linux andy-desktop 2.6.22-13-generic #1 SMP Thu Oct 4 17:18:44 GMT 2007 i686 GNU/Linux
```

Note the SMP in the middle.
If yours does not appear similar we can provide advice on how to fix that :)

---

### Post by technomaniac on 2007-10-23
i have a intel core 2 duo.which version of ubuntu do i install to enable multicore support

---

### Post by sayuki288 on 2007-10-23
i wish i had a quad core too :lolflag:

---

### Post by wheredidrealitygo on 2007-10-24
> "i have a intel core 2 duo.which version of ubuntu do i install to enable multicore support"

it doesn't matter which "version" of Ubuntu you install (I'm assuming you mean the difference between Ubuntu, Kubuntu, Xubuntu, Gobuntu/other non-official distributions), the key for [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing") support is to use a generic kernel, and not an i386 kernel.

all versions have the ability to use a kernel which supports multi-core systems.

---

### Post by realvz on 2007-10-24
as wheredidrealitygo   mentioned...SMP kernel should work for you fine..

---

