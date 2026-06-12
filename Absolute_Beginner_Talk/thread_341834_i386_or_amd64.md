---
title: "i386 or amd64?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by adityak_28 on 2007-01-19
my friend gave me ubuntu 6.06 amd64 cd. while going through the common questions - community ubuntu documentation at [https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions) i came across this:

"I have an AMD64 processor, should I install the i386 ISO or the amd64 one? What are the drawbacks of having an amd64 install?

AMD64 is an officially supported architecture with its respective ISO for Ubuntu and all major Ubuntu derivatives. By installing the amd64 ISO, rather than the i386 (32-bit) ISO, there will be some enhancement in performance.

The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages on your AMD64 install. This is a problem for users who wish to use Flash, w32 codecs, and WINE (for example), as they are only available for 32-bit. There are possible methods of getting it running, but they involve creating a chroot (see DebootstrapChroot), for example."

my machine uses amd x2 3600+ processor (64 bit dual core). considering the fact that i'm a newbie and that i would mostly be using ubuntu for home applications (internet and movies) is it wiser to install the i386 or the amd64 version? or do i have to get 6.10?

---

### Post by johnnymac on 2007-01-19
I too have an amd64 system - I myself use 64-Bit Ubuntu; however, it isn't really necessary.  You really won't see a performance issue really - you'd see an increase in performance if you had an application that supported 64-Bit and ran a 64-Bit OS...but 32-bit is fine.  As a matter of fact, most rather the 32-bit because there's more software supported.

---

### Post by adityak_28 on 2007-01-19
ok. so it would be better to get the i386 version in that case. thanks! i like your avatar btw...

---

### Post by johnnymac on 2007-01-19
Yes...going 32-bit would save you some headache - but there's always that "Hey I'm Cool" factor of saying you run 64-bit.  Ouside of that - no real reason as of yet.

The avatar....yes - I'm the codemonkey :)

---

### Post by Clancy_s on 2007-11-13
Hi,

I'm preparing to install ubuntu on a brand new laptop with an Intel Core 2 duo processor, and I've been trying to decide whether to go with 32 bit or 64 bit: I've been through most of the guides, in some places it says 32 bit, others recomment the 64 bit.

For me the most important bit will be what software is supported: I'll want Flash and the win32 codecs for certain, possibly WINE.  The docs currently only go up to 7.04 (fair enough it takes time), I'm wondering if this bit is still current:

> The drawbacks are that Ubuntu, with APT (the package manager for Ubuntu), currently does not support BiArch, which means you likely won't be able to install and run 32bit packages on your AMD64 install. This is a problem for users who wish to use Flash, w32 codecs, and WINE (for example), as they are only available for 32-bit. There are possible methods of getting it running, but they involve creating a chroot (see DebootstrapChroot), for example.

I don't want to have to get involved with any really tricky stuff first up, so does anyone know if the BiArch problem remains with 64 bit for release 7.10?

Thanks for your help

C

---

### Post by Paul820 on 2007-11-13
> I'll want Flash and the win32 codecs for certain, possibly WINE

All supported, and so is just about every other application that you will need. I have not found one yet that **isn't** supported.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-13
i have been useing 64-bit ubuntu for more that a year the only thing i have had problems with is skype but thats there fault not ubuntus 

if you dont wanna get involved with anything tricky stay away from wine (both on 32-bit and 64) other then that every thing will work fine
and wine is not that bad as long as the program your running isn't a higher end game

---

### Post by rudeboyskunk on 2007-11-13
Just remember:  All computers will have to be 64-bit by 2038.

[http://en.wikipedia.org/wiki/Year_2038_problem](http://en.wikipedia.org/wiki/Year_2038_problem)

---

### Post by Inxsible on 2007-11-13
Go through all of these links and you will be in a better position to answer your own question

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by nutz on 2007-11-13
Go for i386...

The 64bit does have its uses but you will likely never rely on them. And the i386 is a much smoother install and setup for the same reasons other people here have stated.

---

### Post by Inxsible on 2007-11-13
> **nutz said:**
> Go for i386...

The 64bit does have its uses but you will likely never rely on them. And the i386 is a much smoother install and setup for the same reasons other people here have stated.
I installed 64 bit and had no problems whatsoever. In fact my suspend and hibernate worked out of the box. They did not work when I was using 32 bit Feisty.

It would be much better if you read all the links, and make a decision yourself. or if you have space install both OS'es and find out for yourself :D

---

### Post by nutz on 2007-11-13
> **Inxsible said:**
> I installed 64 bit and had no problems whatsoever. In fact my suspend and hibernate worked out of the box. They did not work when I was using 32 bit Feisty.

It would be much better if you read all the links, and make a decision yourself. or if you have space install both OS'es and find out for yourself :D

That is a very valid point; he should try both and decide for himself. I used the 64bit version on a friends PC recently and it didn't turn out nearly as well as the i386 so we ended up formatting it and going back to the i386. But that is the only personal experience I have with the 64bit version.

---

### Post by Clancy_s on 2007-11-13
> **rudeboyskunk said:**
> Just remember:  All computers will have to be 64-bit by 2038.

I hope to have another pc by then. ;)

> **Inxsible said:**
> Go through all of these links and you will be in a better position to answer your own question

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

*heads off with a packed lunch*

> **nutz said:**
> Go for i386...

The 64bit does have its uses but you will likely never rely on them. And the i386 is a much smoother install and setup for the same reasons other people here have stated.

Thanks for all the input, I'll look at the links and get myself sorted by the weekend. :)

eta: I'll try the live CD for both first and see how that goes.  I plan on leaving a spare partition for another OS so I could always install both and see how they go (320Gb HDD).

btw, I'm a her. :)

---

