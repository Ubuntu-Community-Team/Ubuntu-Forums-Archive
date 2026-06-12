---
title: "[SOLVED] Offline install of amd64 gutsy-proposed package"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by david-c on 2007-11-03
Hi,
I have a problem connecting to the internet with my amd64 pc after installing gutsy. Googling I found that it may be bug #156720. The network/internet forum post [http://ubuntuforums.org/showthread.php?t=581055&page=11]("http://ubuntuforums.org/showthread.php?t=581055&page=11")  suggests upgrading libc6 from 2.6.1-1ubuntu9 to 2.6.1-1ubuntu10 by enabling gutsy-proposed in the software sources and using Update Manager to download it.

My question is how do I do this when I have Internet/network problems:confused:
I do have access to a 32bit pc also running gutsy with no internet problems that I can use to download packages, but as a noob I do not know how.  Help please:)
David

---

### Post by haldean on 2007-11-03
download this: [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb) on someone else's computer, save it to a USB stick or something, double click it in Nautilus and press install. I don't know if that will fix your networking problems, but it will install libc6 2.6.1-1ubuntu10 :)

---

### Post by david-c on 2007-11-03
Thanks Haldean,
I will try it out when I get home tomorrow. I checked out the Ubuntu pool and discovered pandoras box! So I am now confused. I have an amd64 system, so instead of installing libc6_2.6.1-1ubuntu10_i386.deb, I would naively believe that perhaps either libc6-amd64_2.6.1-1ubuntu10_i386.deb, or libc6-i386_2.6.1-1ubuntu10_amd64.deb, or even libc6_2.6.1-1ubuntu10_amd64.deb might be a better choice.
My new question is which 2.6.1-1ubuntu10 is best?
Cheers,
David

---

### Post by haldean on 2007-11-04
That's a good point :D Um... avoid the ones with i386 in the name, because that typically refers to 32 bit processors. I would go for the last one.

---

### Post by david-c on 2007-11-04
Cheers Haldean,
I owe you one:)
David

---

