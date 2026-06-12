---
title: "Stuck on Breezy"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by bearlevi on 2008-01-16
I am a recent linux convert, but the only distro I can get working on my machine is Ubuntu 5.10 Breezy Badger. This is no longer supported so I cannot get software updates. I have tried installing a ton of other distros and the computer just won't take them.

I cannot run apt-get update or apt-get upgrade (lack of mulitverse and universe packages error). Everything works fine, but there are some installs I would like to make.

Can anybody help??

---

### Post by SOULRiDER on 2008-01-16
IMHO Breezy wont get you anywhere. What are the problems you get with other distros?

---

### Post by Sef on 2008-01-16
1) Can you update to Dapper Drake, 6.06?  System > Administration > Update Manager

2) What are your system specs?

---

### Post by bearlevi on 2008-01-16
Naw the other distros all freeze up on me. I am running an Averatec notebook 3700 series with 1 GB RAM. I have read that these computers have trouble with linux which is why I had to dig through my archive to find the breezy copy because thats all that will install.

---

### Post by bearlevi on 2008-01-16
It seems that the packages sources for updating or upgrading just give a long error message, same happens when working from the command line.

---

### Post by bollix47 on 2008-01-16
> **bearlevi said:**
> I am a recent linux convert, but the only distro I can get working on my machine is Ubuntu 5.10 Breezy Badger. This is no longer supported so I cannot get software updates. I have tried installing a ton of other distros and the computer just won't take them.

I cannot run apt-get update or apt-get upgrade (lack of mulitverse and universe packages error). Everything works fine, but there are some installs I would like to make.

Can anybody help??

Re lack of multiverse and universe have a look [here]("http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories").

---

### Post by bearlevi on 2008-01-16
> **bollix47 said:**
> Re lack of multiverse and universe have a look [here]("http://ubuntuguide.org/wiki/Ubuntu#How_to_add_extra_repositories").

Yeah I looked at that yesterday and I editted my sources.list to reflect the wiki file, but even after doing that I cannot update. I get the errors saying the packages cannot be accessed. 
Thanks though.

---

### Post by t0p on 2008-01-16
This reply may get me lynched, but I'll risk it.

I think that running an unsupported version of an OS is a bad idea.  You can't get support which means you get no security updates.  Your system may be riddled with vulnerabilities that you can't do anything about, so you could end up with your box getting pwned.  Plus there are other problems with an unsupported OS - your inability to use apt-get or Synaptic for instance.

So, I think you'd be better off checking out other distros, see if you can find something recent and actively supported that works on your computer.  Many distros have live CDs nowadays, so checking for compatability is dead easy.

I know Ubuntu's the best.  But, if it doesn't work, it doesn't work.  Much better to find another distro - Linux is the greatest all-round. ;)

---

### Post by TheOrangePeanut on 2008-01-16
Where exactly does the freezing happen?  Can you kill xserver?  Have you tried booting with "safe graphics mode"?

---

### Post by bearlevi on 2008-01-16
I can get the Dapper Drake 6.06 to boot the live cd, but when I try to install to the HD, I can get through the setup, but after the partition configuration it stalls at about 28%. The CD checked out, but it maybe a mem issue. 

any ideas to help me get this one working?

---

### Post by TheOrangePeanut on 2008-01-16
Have you ran memtest on the machine?  Have you tried the alternate CD install (instead of the livecd)?

---

### Post by bearlevi on 2008-01-16
I had several mem test failures but that was testing only Gutsy. i'll try it with Dapper, but if it is a mem test failure is there any hope? is it new computer time?

---

### Post by bearlevi on 2008-01-16
I have tried the alternate cd, and the freeze still happens.

---

### Post by meindian523 on 2008-01-16
maybe,but not necessarily.Can this problem occur if you mix and match various types of memory on your board?Maybe you upgraded your memory and didn't pay attention to what kind the old RAM in the other slot was?

---

### Post by TheOrangePeanut on 2008-01-16
If you're getting memtest failures then there is definitely a problem.  I would suggest taking out all but one stick of ram and testing them one by one to see which of them are bad.  It's probably not new computer time, but it could be new ram time :)

---

### Post by bearlevi on 2008-01-16
haha that could be fun, more stuff to play with

---

### Post by bearlevi on 2008-01-16
ok ran a mem test with the dapper liveCD and passed

---

### Post by bearlevi on 2008-01-16
so I ran md5sum -c md5sum.txt to check mismatched checksums (not that I got that error, but it couldn't hurt to check)

and I got an output saying 12 of 414 files could not be read. is it a bad burn? should I get another copy of Dapper?

---

### Post by meindian523 on 2008-01-16
1]md5sum check your **ISO**.
2]Burn at 4x,preferably on CD-R,not CD-RW.

---

### Post by Paulmd on 2008-01-16
> **bearlevi said:**
> I can get the Dapper Drake 6.06 to boot the live cd, but when I try to install to the HD, I can get through the setup, but after the partition configuration it stalls at about 28%. The CD checked out, but it maybe a mem issue. 

any ideas to help me get this one working?

1) Have you tried the alternate text-based install cds? 
2) If it is a memory issue, you can test that with memtest86+ which comes with most linux distros. It is also available as a standalone product.

---

