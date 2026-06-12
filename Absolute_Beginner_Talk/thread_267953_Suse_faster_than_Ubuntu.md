---
title: "Suse faster than Ubuntu?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-09-29
Hi all,
I recently found out that i could improve my hard-drive performance using hdparm. I loved the tool..tinkered as instructed on many web-sites by enabling dma, multcount. However, in most cases, the results were the same. In some, they were even worse. 
On an average..i get Buffered reading speed as 11 Mbps..
I tried hdparm on suse 10.0 on another partition..and i get the buffered read speed as 30 Mbps. The options..as far as i can tell- are the same for both the Oses...
Suse also feels much faster.

Is it true that Ubuntu on my machine will never be as fast as Suse? I really like ubuntu and dont want to switch to another OS..but i want a fast OS too .. :(

---

### Post by dca on 2006-09-29
On my laptop, Ubuntu's start-up time is way faster than openSuSE.  70secs vs > 40 secs...  The problem(s) I had w/ suse were all relative to YaST...  My goodness, it would take forever for it to open services, etc.

---

### Post by steve.horsley on 2006-09-29
I wonder if the fact that SUSE defaults to reiserfs instead of ext3 is making a difference.

---

### Post by shahgols on 2006-09-29
Does ubuntu support reiserfs?

---

### Post by skymt on 2006-09-29
> **shahgols said:**
> Does ubuntu support reiserfs?

Yes. It's what I use. You have to pick it when you install.

---

### Post by shahgols on 2006-09-29
Thanks sky.

---

### Post by justin whitaker on 2006-09-29
> **kitt said:**
> Hi all,
I recently found out that i could improve my hard-drive performance using hdparm. I loved the tool..tinkered as instructed on many web-sites by enabling dma, multcount. However, in most cases, the results were the same. In some, they were even worse. 
On an average..i get Buffered reading speed as 11 Mbps..
I tried hdparm on suse 10.0 on another partition..and i get the buffered read speed as 30 Mbps. The options..as far as i can tell- are the same for both the Oses...
Suse also feels much faster.

Is it true that Ubuntu on my machine will never be as fast as Suse? I really like ubuntu and dont want to switch to another OS..but i want a fast OS too .. :(

Well, speed is relative. You can run Gentoo and get above 30mbps reads, but not get any work done, you know?

SuSE picked up the lead project manager from Yoper before 10.0, because one of the knocks on SuSE was that it was dog slow (it was). There are a bunch of tricks that Yoper, and now SuSE, used to make the whole thing faster:

1. Prelinking. Alot of KDE and other apps on SuSE have been prelinked, so that it loads faster. You can use prelink to do the same thing on your system.

2. CFlags: like Gentoo and Vector, SuSE plays with the CFlags to get better compiling optimizations when generating RPMs. You can use [apt-build]("http://julien.danjou.info/article-apt-build.html") to generate optimized debian packages for your system, and you can reset your GCC configuration to optimize code you compile yourself. Pass apt-get -b source appname and you will generate optimized code. 

3. Optimized kernels-SuSE supports primarily recent hardware, while Ubuntu tries to be more inclusive. I'm not sure if the SuSE kernel uses the CK patch or not. Patch and recompile your kernel if performance is that important to you. 

Personally, all that seems like alot of work for very little gain, but if it is important to you, go for it!

---

### Post by nudnik on 2006-09-29
> **dca said:**
> On my laptop, Ubuntu's start-up time is way faster than openSuSE.  70secs vs > 40 secs...  The problem(s) I had w/ suse were all relative to YaST...  My goodness, it would take forever for it to open services, etc.

I had the same experience with YAST, which was broken (openly admitted on their website) and took forever to load with numerous errors in the process. I eventually hammered it into submission, but it remained mind numbingly slow to the end. When I have time I will see if I can get the thing to speed up by experimenting with different configurations.

The above being said, SUSE has a fantastic default X configuration.

Ubuntu runs slightly slower than XP Professional on my machine, but not by much. 

Specs:
Pentium 820D
Intel 945PSN MB
1GB 533 DDR2
80GB SATAII
Nvidia 7300GS 256MB

---

### Post by kitt on 2006-09-30
> Well, speed is relative. You can run Gentoo and get above 30mbps reads, but not get any work done, you know?

SuSE picked up the lead project manager from Yoper before 10.0, because one of the knocks on SuSE was that it was dog slow (it was). There are a bunch of tricks that Yoper, and now SuSE, used to make the whole thing faster:

1. Prelinking. Alot of KDE and other apps on SuSE have been prelinked, so that it loads faster. You can use prelink to do the same thing on your system.

2. CFlags: like Gentoo and Vector, SuSE plays with the CFlags to get better compiling optimizations when generating RPMs. You can use apt-build to generate optimized debian packages for your system, and you can reset your GCC configuration to optimize code you compile yourself. Pass apt-get -b source appname and you will generate optimized code.

3. Optimized kernels-SuSE supports primarily recent hardware, while Ubuntu tries to be more inclusive. I'm not sure if the SuSE kernel uses the CK patch or not. Patch and recompile your kernel if performance is that important to you.

Thanks for all these tricks..
But, im having a hard time understanding how Suse is able to make better use of my hard-ware with the same settings (refer to my 1st post on the thread)..
I can understand code optimization and all that stuff- but how can Suse manage 30Mbps read speeds *during heavy loads* and ubuntu struggles at 5 Mbps during load. 
One more thing- i tried the hdparm test after shutting down GDM..and i got 31MBps speeds..SO can i conclude that Suse is somehow able to manage multitasking much better? 
I even use the K7 Kernel on my ubuntu..and it doesnt speed up anything :(

---

