---
title: "HOWTO: Give your PPC Mac that 25%+ boost w/FreeVec"
date: 2009-09-11
forum: Apple Hardware Users
---

### Post by Frak on 2009-09-11
First and foremost
[CENTER][COLOR="Red"][SIZE="5"]THIS GUIDE IS PROVIDED "AS-IS", NO WARRANTY, ETC. ETC.
THIS IS INTENDED FOR PowerPC MACHINES ONLY! THIS WILL *NOT* WORK ON INTEL MACINTOSHs. THIS *SHOULD* WORK ON ALL G4s.[/SIZE][/COLOR]

Due to the fact that PowerPC's did not as of yet support the AltiVec instruction set, this will not work on PowerPC G3s. This *may* work on PowerPC G5's, but I have heard of issues with PPC64 machines. This works, nearly flawlessly on all G4-based Macintoshs.

I am assuming that the audience reading this has a basic knowledge of compiling software.[/CENTER]

[FreeVec]("http://www.freevec.org/"), a (LGPL) library with replacement routines for GLIBC, such as memcpy(), strlen(), etc. These routines, which have been rewritten and optimized to use the AltiVec vector engine found in the G4/G4+ PowerPC CPUs, can provide for up to 25% increase in application performance.

Traditionally, you would recompile your entire system to use the libfreevec library. While recompiling is my preferred way, but there is a much easier, much faster method to implementing the powerful FreeVec instructions instead of using the default AltiVec instructions. Well, little known that FreeVec includes a libc library replacement for AltiVec that implements a much more optimized set of instructions. Let's start...

First, make sure [_build-essential_]("apt:build-essential") is installed on your system.

Secondly, download libfreevec (due to it being IMPOSSIBLE to find on the internet, I'll link it on the end of the post).

Extract libfreevec somewhere on your hard-drive.
```
tar xfj libfreevec-1.0.4.tar.bz2
```

Change into the directory containing the libfreevec source.
```
cd libfreevec-1.0.4
```

Configure
```
./configure --prefix=/usr
```

Compile
```
make
```

Install
```
sudo make install
```

Now we add the libc library to the ld preloader. For this, we will be using an application called [_ld.so.preload-manager_]("apt:ld.so.preload-manager").
```
sudo ld.so.preload-manager /usr/local/lib/libfreevec_libc.so
```

It will prompt you to acknowledge that you want to add that library to the ld.so.preload file, confirm this.

Reboot and it should work. I haven't got a command right now to test if it is indeed running, but I seem to see a huge difference in speed. A movie I couldn't watch before is now fully viewable with minimal skips. Maybe it's just timing, but I can definitely see a difference in performance.

---

### Post by gwydionwaters on 2009-09-15
apparently i don't have ld.so.preload-manager on 8.10 ?

---

### Post by Frak on 2009-09-15
> **gwydionwaters said:**
> apparently i don't have ld.so.preload-manager on 8.10 ?
Try running

```
sudo echo /usr/local/lib/libfreevec_libc.so > /etc/ld.so.preload
```

And post if it succeeds or not.

---

### Post by gwydionwaters on 2009-09-16
i got permission denied, but su'd and it worked. well there was not any error that is, entered 
echo /usr/local/lib/libfreevec_libc.so > /etc/ld.so.preload

***
so i have an error,
saying that the preload could not be preloaded, the bubble suggested a dependency was not met, so i am installing build-essentials, which i previously assumed i had. i'll try again and post :)

***
ok, so it still gives me an error
```
ERROR: ld.so: object '/usr/local/lib/libfreevec_libc.so' from /etc/ld.so.preload cannot be preloaded: ignored.
```

---

### Post by Frak on 2009-09-16
The latest update sorta bork'd it. Just remove it from your preload. I think the dev beyond that has abandoned it.

---

### Post by gwydionwaters on 2009-09-16
ya i did that, thats a shame. a performance boost would be nice

---

### Post by rbertran on 2009-11-24
The libmotovec library provided by freescale might be useful too. I have not tested it yet. You need to register first, to be able to download them.

[http://www.freescale.com/webapp/sps/site/overview.jsp?nodeId=02VS0l81285Nf2d9nb]("http://www.freescale.com/webapp/sps/site/overview.jsp?nodeId=02VS0l81285Nf2d9nb")

---

### Post by rednose0607 on 2009-11-26
Hi,
tryed it. I confirm no ld.so.preload* stuff, then added to my yaboot.conf append "LD_PRELOAD=<path to lib>"

I have a lot of warnings on boot about ld.so not being abel to load the library. BTW it installs in /usr/lib/freevec.

I can't see/say if perf improving .... :confused::confused:

I guess I'll switch back :-/

---

### Post by robyinno on 2009-11-30
On my Ubuntu 9.04 on my G4 1.33 Ghz I have installaed freevec.
Unitil sudo make install all is the same of your guide.

For install ld.so.preload-manager:

sudo aptitude install ld.so.preload-manager

The libfreevec is installed ( by make install) 
in /usr/lib/freevec/libfreevec.so

so for preload you need to do
sudo ld.so.preload-manager /usr/lib/freevec/libfreevec.so

After I have rebooted and every look like more responsive and fast!

Thank you!

---

