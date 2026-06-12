---
title: "eee pc 1015PEM diagnosing slow cpu"
date: 2012-08-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by sousedstvi on 2012-08-29
Hi,

My installation of 12.04 (64-bit) sometimes becomes uselessly slow and I have to power it down. When I notice it being slow, I look at top (if I can even switch windows to my terminal) and see load averages pushing 6,7,8. Meanwhile, top does not show any single process taking up a high percentage of CPU.

this massive paralysis typically happens when browsing the web (chrome or firefox); for example, when I try to scroll down a page that is still loading. But maybe that's only because I mostly use the computer for web browsing.

I'm dual-booting win7 and installed ubuntu (at 11.04, I think) using the windows ubuntu installer (wubi). I don't use the windows 7 install much, but I haven't noticed this problem on that side.

other details:
memory: 985.6 MiB
processor: Intel Atom CPU N550 @ 1.50GHz x 4
64-bit

thanks,
christopher

---

### Post by sousedstvi on 2012-09-04
I noticed from top that while the load average was creeping up (sometimes to 15!) that the swap was totally used up. I think it was 250 Mb (or so). I decided that might be the problem, so I increased the size of the swap file (not a partition, I guess that's how wubi sets it up) to 1Gb using [these instructions]("https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F"). THat has seemed to help for the past few hours.

---

### Post by shadedpixel on 2012-09-08
> **sousedstvi said:**
> I noticed from top that while the load average was creeping up (sometimes to 15!) that the swap was totally used up. I think it was 250 Mb (or so). I decided that might be the problem, so I increased the size of the swap file (not a partition, I guess that's how wubi sets it up) to 1Gb using [these instructions]("https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F"). THat has seemed to help for the past few hours.
Thats good to know, ill keep that in mind if I ever run into this.

---

