---
title: "Running 32bit binary from Trusty on 64bit Aardvark. Issues with libudev.so.1"
date: 2018-04-22
forum: Apple Hardware Users
---

### Post by wowfunhappy on 2018-04-22
I have closed source binary that works on 32bit installations of Ubuntu Trusty. I'm trying to get it to run on a fresh installing of 64bit Aardvark.

After installing lib32gcc1, trying to run the binary results in:
```
 error while loading shared libraries: libudev.so.1: cannot open shared object file: No such file or directory
```
Installing libudev1 (and libudev0, for good measure) did not fix the error.

As a test, I tried copying libudev.so.1 from /usr/lib/x86_64-linux-gnu into the same directory as the executable. This resulted in a different complaint from the executable:
```
error while loading shared libraries: libudev.so.1: wrong ELF class: ELFCLASS64
```

For the heck of it, I tried copying 32bit trusty's copy of libudev.so.1 into the directory of the executable. This got the program to start, but it promptly crashed.

I'm kind of stuck. Is there anything else I can try to make this program work?

---

### Post by kerry_s on 2018-04-22
whats your specs? can you run a 32bit install in a vm?

---

### Post by wowfunhappy on 2018-04-23
I'm on a 2012 Macbook Air. I can use a VM, or I can just reboot&#8212;but I'd like to not have to.

---

### Post by wildmanne39 on 2018-04-23
*Thread moved to **Apple Hardware Users for a more appropriate fit**.*

---

### Post by wowfunhappy on 2018-04-23
I did a test on 32bit Ubuntu Aardvark, and the binary worked. So, this issue is entirely due to the fact that I'm using the 64bit release. I'd really like to make the program work there, though!

---

### Post by &amp;KyT$0P# on 2018-04-23
You need to figure out what all 32-bit libraries it requires, then install the Aardvark packages of those 32-bit libraries using a command like this -
```
sudo apt-get install <lib1>:i386 <lib2>:i386
```

This command might help you figure out what libraries it needs -
```
objdump -p <your closed source binary> | grep NEEDED
```

---

### Post by wowfunhappy on 2018-04-26
Thank to everyone for their help.

The packages I needed ended up being libudev-dev:i386 and libasound2:i386. I recommend trying just the former of these packages initially.

---

### Post by wowfunhappy on 2018-04-29
Seems I jumped the gun a bit...

This software makes use of Bluetooth, and is unusual in that it handles device pairing internally. On newer versions of Ubuntu with the previously mentioned packages installed, the application runs and the pairing process initially appears to work, but the Bluetooth devices are never able to connect.

As far as I can tell, connection is successful in and only in Ubuntu Trusty Tahr. I have tested Ubuntu 17.10 Aardvark, Bionic, and Xenial on two different, real machines as well as a VM. In all cases, I was able to successfully pair a standard Bluetooth speaker via the OS, so I know that Bluetooth itself worked properly.

I realize we're taking a bit of a shot in the dark since we don't know what's wrong, but are there any other compatibility libraries I could try? Or will I need to always reboot into Ubuntu Trusty?

Thanks!

---

### Post by wowfunhappy on 2018-04-30
Would **chroot** have a decent chance of working for something like this? Setting it up looks somewhat involved, so I don't want to try unless there's a moderate chance of success. I already feel like I've dedicated an inordinate amount of time to this...

---

