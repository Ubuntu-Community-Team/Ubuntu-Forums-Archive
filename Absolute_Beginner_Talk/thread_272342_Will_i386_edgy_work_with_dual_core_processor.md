---
title: "Will i386 edgy work with dual core processor?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by NoTiG on 2006-10-06
this may be a stupid question but can 32 bit OS edgy utilize dual cores?

---

### Post by brt on 2006-10-06
as the default kernel has smp support it will run perfectly :D

---

### Post by jmwyatt on 2006-10-17
Made the upgrade from Dapper to Edgy... Everything is beautiful except it shows only one processor (AMD64 X2 3800+). Any thoughts regarding how I can get Edgy to recognize both cores? Should I install Edgy AMD64?

---

### Post by Aberrix on 2006-10-17
I run 6.06 i386 on my X2 3800 dual core with no problems at all.

---

### Post by jmwyatt on 2006-10-17
It runs... It just doesn't show two cores. 

Should I upgrade the kernel to something other than 386? If so, how?

---

### Post by bulldog on 2006-10-17
This link explain somethings for you and works good in Dapper,it should do in Edgy.

[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

---

### Post by Aberrix on 2006-10-17
> **bulldog said:**
> This link explain somethings for you and works good in Dapper,it should do in Edgy.

[http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

thanks for the link!

---

### Post by jmwyatt on 2006-10-17
My confusion started when I downloaded and ran the 6.10 beta AMD64 live iso. When I boot from the CD, both processors show up. I didn't think Edgy was going to have an AMD64 version (SMP would run in the 3856 version and that was going to be the only one -- no k7, smp, 686, etc.)

So, the questions are: How do I upgrade to the AMD64 Edgy version? Do I need to? (Should the 386 version work with dual processors, and, if so, why isn't it?) Any help is appreciated! Thnaks!

---

### Post by Aberrix on 2006-10-17
^ With that in mind I've been wondering something myself...

What is the real advantage of using 686 vs. 386?

If I can get the k7-smp kernel working on my 386 install, what is the benefit of running it on 686?

With all the posts I see about getting things to work properly and other things not working properly I don't see to much of a benefit of switching (at the moment).

---

### Post by bulldog on 2006-10-17
Well you have to search for it or ask around in the Edgy forum thread.


I have no clue about Edgy and 64bit.

[http://ubuntuforums.org/forumdisplay.php?f=144](http://ubuntuforums.org/forumdisplay.php?f=144)

---

### Post by artworx on 2006-11-04
A newbie here! I have an intel dual core processor and i wnat to install edgy eft. after selecting "install ubuntu server on hard disk", the following message appears "uncompressing linux... booting the kernel" and nothing else happens. i tried installing it on my old PC & it works fine so there's nothing wrong w/ my CD. is there a workaround for this? TIA!

---

### Post by Lord Illidan on 2006-11-04
Edgy works fine on Pentium D dual core.. I think I installed the smp kernel.

---

### Post by artworx on 2006-11-04
Thanks for the reply! But how do i install the SMP kernel?

---

### Post by bulldog on 2006-11-04
Your Edgy should use the 'generic' kernel by default and it supports dual core.

Try ```
uname -a
``` in your terminal to see which kernel you use.

---

