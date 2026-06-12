---
title: "Is 64-bit Ubuntu 7.04 Better? Necessary? Recommended?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Curbuntu on 2007-08-13
Well, I survived a mess left by a failed WUBI install (messed up MBR) and I've now finally finished and submitted a book manuscript that has been hanging over my head for weeks.  Without that out of the way, I dared not try any kind of install that required dual-boot disk partitioning "just in case."

But now it's nearing time to take the plunge and dual-boot my laptop with Ubuntu Feisty Fawn.  I had downloaded the standard "Live CD" for Intel 386 architecture, when I discovered that there's a Live CD version for 64-bit CPUs.  My Compaq laptop has an AMD-64 Athlon 3400+ (runs at 2.2 GHz, 1 Mb L2 cache) and has a gig of RAM and has been upgraded to a 120 Gb HDD.

So the questions are:[LIST=1]
[*]Should I eschew the standard 386-based install in favor of an Ubuntu optimized for 64-bit processors?  Will there be that much difference in performance, compatibility, etc.?  And,
[*]Will there be any more-or-less standard Ubuntu apps that won't be able to run under the 64-bit version of Ubuntu?  (I'm not yet savvy enough to even specify apps, but I am wondering about VirtualBox specifically.)[/LIST]

---

### Post by Bachstelze on 2007-08-13
Stick with 32bit. With 64bit you will get no significant performance gain, but you will lose much software compatibility (Flash Player or some multimedia codecs, for example).

---

### Post by SNYP40A1 on 2007-08-13
Use 64-bit when you actually need 64 bits of precision (scientific computing) or have more than 4 GB of memory.  In other words, if you have to ask, you don't need it.

---

### Post by jimrz on 2007-08-13
> **Curbuntu said:**
> Well, I survived a mess left by a failed WUBI install (messed up MBR) and I've now finally finished and submitted a book manuscript that has been hanging over my head for weeks.  Without that out of the way, I dared not try any kind of install that required dual-boot disk partitioning "just in case."

But now it's nearing time to take the plunge and dual-boot my laptop with Ubuntu Feisty Fawn.  I had downloaded the standard "Live CD" for Intel 386 architecture, when I discovered that there's a Live CD version for 64-bit CPUs.  My Compaq laptop has an AMD-64 Athlon 3400+ (runs at 2.2 GHz, 1 Mb L2 cache) and has a gig of RAM and has been upgraded to a 120 Gb HDD.

So the questions are:[LIST=1]
[*]Should I eschew the standard 386-based install in favor of an Ubuntu optimized for 64-bit processors?  Will there be that much difference in performance, compatibility, etc.?  And,
[*]Will there be any more-or-less standard Ubuntu apps that won't be able to run under the 64-bit version of Ubuntu?  (I'm not yet savvy enough to even specify apps, but I am wondering about VirtualBox specifically.)[/LIST]

unless you need to run some progs that actually need / can utilize the 64 bit capabilities (and there currently are very few of these), I would go with the 32 bit as it seems to have way fewer issues than the relatively new 64 bit which seems to be going through some growing pains

---

### Post by avik on 2007-08-13
Personally, I like 64bit, and just about everything that's available for 32bit (yes, [even flash]("http://ubuntuforums.org/showthread.php?t=476924")) is available for 64bit.  But it's true, unless you need something only a 64bit OS can provide, especially if you're new to Ubuntu), you'll want to use the 32bit version.

---

### Post by jw5801 on 2007-08-13
I use 64-bit purely because I can... :p
It does offer a fairly significant improvement on any iterative processes (like encoding music/video, or numerical stuff), but only if the program you're running to do this is compiled for 64-bit. I haven't noticed any major difficulties with 64-bit apart from Java, but if you know what to install then that works well too.

---

### Post by RomeReactor on 2007-08-13
Hi. I agree with most here in that 64 bit, in a common user's day, will offer you very little over 32 bit. Unless you constantly use processor intensive applications (like video demuxing/transcoding or similar processes), you probably won't need it, particularly with 2GB RAM or less of system memory. That said, I just recently installed the 64 bit version (after trying it about a year ago for a few weeks and using 32 bit the rest of the time) and it is a _little_ bit faster for me, even with a Sempron 2800+ and the 1 GB RAM I have on my system, and it is stable. F-Spot is noticeably faster, even with a collection of 24,000 + pictures.

And yes, the [flashplayer script by Kilz]("http://ubuntuforums.org/showthread.php?t=476924") works flawlessly.

---

### Post by st33med on 2007-08-13
> **SNYP40A1 said:**
> Use 64-bit when you actually need 64 bits of precision (scientific computing) or have more than 4 GB of memory.  In other words, if you have to ask, you don't need it.

Wow! I never knew that! Where'd you get that piece of info?

EDIT: looked up on Wikipedia. 

> A 32-bit register meant that 2^32 addresses, or 4 gigabytes of RAM, could be referenced

And if we were to make a 128-bit processor?

> The emergence of the 64-bit architecture effectively increases the memory ceiling to 264 addresses, equivalent to 17,179,869,184 gigabytes or 16 exabytes of RAM

Yeeeaaaahhhh... No memory device today could even get to an extabyte. 16-bit had a ceiling of 64 *kilo*bytes and 8-bit was 256 bytes.

---

### Post by Curbuntu on 2007-08-14
Thanks to all of you for your replies.  I rather suspected that the 64-bit version might be overkill for the moment.  But at the rate hardware evolves, it may not be long before we're all using the 64-bit version and thinking nothing of it.

Meanwhile, the 32-bit Intel386 Live CD it is...

---

### Post by st33med on 2007-08-14
So, if you really wanted to expose a 64-bit's true power, this is the only memory module I could find that is above 4 Gigs on Newegg

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820144074]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820144074")

And only $539.99!!! So affordable, I could buy another (cheap) laptop!

---

