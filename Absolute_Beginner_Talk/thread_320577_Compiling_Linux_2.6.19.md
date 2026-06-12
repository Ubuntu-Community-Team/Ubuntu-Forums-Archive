---
title: "Compiling Linux 2.6.19"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by kcallis on 2006-12-17
I have been trying to compile 2.6.19 successfully. Although I am able to compile and load, after a period of time, I get a panic. I believe that part of the problem is that the acpi isnt loading correctly, and the system locks up when there is too much heat. Another thing that I realized is that although I load the acpi, I notice that when I would reboot, I no longer had an option to hibernate the laptop. Although  I should point out that when I am running the 2.6.17-generic (default kernel), it works just fine.

When I downloaded the sources for 2.6.17, I noticed that there was some mention of ubuntu patches applied to the kernel. Do I need to figure out what the patches are, and apply them to 2.6.19? I copied the .config from 2.6.17-generic over to 2.6.19, but I think I am doomed to failure.

Has anyone rolled 2.6.19, and if so, would you tell me what the trick is to get that working correctly.
](*,)

---

### Post by zgornel on 2006-12-17
Appling the [beyond]("http://iphitus.loudas.com/beyond.html") patch and using the 2.6.17-generic config should cover most of the ubuntu patches. Some drivers might be left out but you should not worry.

---

### Post by kcallis on 2006-12-18
I just downloaded 2.6.19.1, and have the patch downloaded as well, but I am not sure now to install it... I am going to assume place patch in /usr/src/linux and do a bzcat patch-2.6.19-beyond2.bz2 | patch -p1, but I just wanted to check and make sure...

---

### Post by kcallis on 2006-12-18
I was feeling suicidal and decided to try and patch the kernel... I ran into reject after reject, so now I am at a loss!

---

### Post by kcallis on 2006-12-18
I have installed the patches and I a still getting the following error:

Message from syslogd@gondor at Mon Dec 18 10:18:58 2006 ...
gondor kernel: [  211.961617] Oops: 0000 [1] SMP 

Message from syslogd@gondor at Mon Dec 18 10:18:58 2006 ...
gondor kernel: [  211.961858] CR2: 0000007478742e41

Message from syslogd@gondor at Mon Dec 18 10:19:52 2006 ...
gondor kernel: [  253.792265] Oops: 0000 [2] SMP 

Message from syslogd@gondor at Mon Dec 18 10:19:52 2006 ...
gondor kernel: [  253.792506] CR2: 0000007478742e41

What can I be doing wrong... The machine is still locking up!!!

Linux gondor 2.6.19-beyond2 #1 SMP Mon Dec 18 02:01:20 PST 2006 x86_64 GNU/Linux

---

### Post by kilou on 2006-12-18
I also tried to compile kernel 2.6.19.1 with the latest beyond2 patch and I keep getting errors as well (not the same though, I don't remember) :( However I did compile the 2.6.19 kernel and it was working OK. Followed that guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

