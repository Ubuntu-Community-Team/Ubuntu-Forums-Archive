---
title: "Whats better 32 or 64 bit"
date: 2008-01-29
forum: Arch and derivatives
---

### Post by mauud777 on 2008-01-29
i will move to arch in a few days

but i am dont now whats butter for me 

64 bit or 32 bit

and whats so special in 64 bit

my cpu : core2due

ram :1 G

can you give me the main problems in 64 bit

---

### Post by CheShA on 2008-01-29
If you can use 64bit, do. 32bit is legacy for older 32Bit CPUs.

---

### Post by mauud777 on 2008-01-29
> **CheShA said:**
> If you can use 64bit, do. 32bit is legacy for older 32Bit CPUs.

thanks man ... whats the Distinguished in 64 bit

and whats butter in performance

---

### Post by CheShA on 2008-01-29
In a nutshell, 32Bit is limited by the 32Bit address space so you get stuck with e.g. only being able to address 4GiB RAM.  64 Bit should give better performance all round under Linux.

Under Windows, because 64 bit is relatively unused, there are problems with driver support and not many applications are made for 64bit (so they run under virtual 32bit space which reduces the benefits of running a 64bit OS.).

With Linux, because it is driven by Computer Scientists' choices rather than by Corporate choices, 64 bit is a mature platform. Because Linux is open source, driver availability and application support is not really a concern because all it takes is to compile the drivers/application for 64 bit, which the Ubuntu repos take care of for you :)  Any programs athat are optimised for 64 bit should run much better than any programs that are optimised for 32 bit would run on a 32 bit platform.

---

### Post by mauud777 on 2008-01-29
> **CheShA said:**
> In a nutshell, 32Bit is limited by the 32Bit address space so you get stuck with e.g. only being able to address 4GiB RAM.  64 Bit should give better performance all round under Linux.

Under Windows, because 64 bit is relatively unused, there are problems with driver support and not many applications are made for 64bit (so they run under virtual 32bit space which reduces the benefits of running a 64bit OS.).

With Linux, because it is driven by Computer Scientists' choices rather than by Corporate choices, 64 bit is a mature platform. Because Linux is open source, driver availability and application support is not really a concern because all it takes is to compile the drivers/application for 64 bit, which the Ubuntu repos take care of for you :)

thanks bro i will install 64 bit

but do you think 1 g ram good for 64 bit

thanks man :KS

---

### Post by aeto on 2008-01-29
For the benefit of others, I feel the need to correct some weird spellings.

thinks = thanks
butter = better

There, you are now understood. You will get better help from [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit) and of course [http://wiki.archlinux.org/index.php/Current_state_of_Arch64_developement](http://wiki.archlinux.org/index.php/Current_state_of_Arch64_developement)

If you want things like Flash and stuff, there is no choice but to chroot or go multi-lib. Thus, there is no point in 64-bit as of now. It highly depends on your purpose of computing. In some situations pure 64-bit is truely worthwhile.

---

### Post by mauud777 on 2008-01-29
> **aeto said:**
> For the benefit of others, I feel the need to correct some weird spellings.

thinks = thanks
butter = better

There, you are now understood. You will get better help from [http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit) and of course [http://wiki.archlinux.org/index.php/Current_state_of_Arch64_developement](http://wiki.archlinux.org/index.php/Current_state_of_Arch64_developement)

If you want things like Flash and stuff, there is no choice but to chroot or go multi-lib. Thus, there is no point in 64-bit as of now. It highly depends on your purpose of computing. In some situations pure 64-bit is truely worthwhile.

thanks man for help :KS

---

### Post by LaRoza on 2008-01-29
(Title changed to avoid puns and confusion)

---

### Post by mauud777 on 2008-01-29
> **LaRoza said:**
> (Title changed to avoid puns and confusion)

thanks man ):P

---

### Post by ryanVickers on 2008-01-29
basically, imagine a 4 lane highway.  This represents 32 bit.  A 33 bit highway would have 8 lanes, a 34 bit would have 16, and so on:

BITS in CPU: - - - - - - LANES on HIGHWAY:
[COLOR=DarkRed]**32 ------------------------------------- 4**[/COLOR]
33 ------------------------------------- 8
34 ------------------------------------- 16
...
62 ------------------------------ 4294967296
63 ------------------------------ 8589934592
[B][COLOR=DarkRed]64 ----------------------------- 17179869184[/COLOR]

[/B]Clearly, its a good choice :D

EXPLANATION:
with 32 bit, you can only address up to 4 GiB of memory, but with 64 bit, you can address up to 16 EiB, [COLOR=black]or [/COLOR][COLOR=black]17179869184 GiB :p
And example of where this comes in handy, is this number sets the maximum amount of RAM you can have (your motherboard would have a limit too though, and no where near as high)

Another thing that relates to this is take "FAT32" for example - a 32 bit filesystem, it can handle no *single* file larger than 4 GiB!
[/COLOR]

---

### Post by steveneddy on 2008-01-29
64 bit is truly the way to go.

Use your hardware to the fullest!

Go 64. You won't regret it.

---

### Post by ryanVickers on 2008-01-29
The whole world is really moving that way, and if you *do* go with 32 bit, then in a few years you'll regret it because it will seem very obsolete.

If anyone else has noticed that the market tends to sway in and out of "pro-64 bitism", the reason for that is that AMD and intel are always swaying over and under each other as which is better, and when intel sways in as the top, since they are very non-64 but at this time, you tend to not see as many chips as you do when AMD comes in.  Perhaps this itself is obsolete information, but from what I've seen AMD tends to make 64 bit a standard feature, where as with intel it's more of a specialty option

---

### Post by steveneddy on 2008-01-29
There are so few 32 bit processors being mass produced anymore that it only makes sense to go with a 64 bit OS to use the modern technology.

---

### Post by mauud777 on 2008-01-30
thanks everyone .... the main problem in 64 bit

The drivers + programs

like : lightscribe :mad:

is there any solution for this problem

do you think 1 G can deal with 64 bit with

Kde + firefox ...etc

---

### Post by aeto on 2008-01-30
yeah, AMD after all was the one who brought 64-bit to the masses. And Linux was 4 to 5 years earlier in adopting the arch than today's most dominant household OS. So in one way, Linux x86_64 _is_ less headache than any 64-bit Windows if talking about driver and software support. Since the Mac handles 64/32 differently in a compromizing method (the kernel can be a 32-bit process), it has no problem either.

---

### Post by ryanVickers on 2008-01-31
Bot sure if this is relevant, but when I got my CPU 18 months ago, AMD was the best around, but I think the markets have switched back to intel for now, what with the Phenom disaster and no one noticing that although the Core 2 Quad's out-class everything in speed, they are in theory built on the same bus as the Duo's and thus half the power is, ... inaccessible ...

---

