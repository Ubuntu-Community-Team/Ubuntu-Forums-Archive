---
title: "Mac with intel core"
date: 2006-06-12
forum: Apple PPC Users
---

### Post by slipk487 on 2006-06-12
which versoin of ubuntu whould u install on a mac with a intel processer the version for windows or the version for mac

---

### Post by colinhayes on 2006-06-12
[QUOTE=slipk487]which versoin of ubuntu whould u install on a mac with a intel processer the version for windows or the version for mac[/QUOTE]

x86 version.

---

### Post by manny_v on 2006-06-13
I am using UBUNTU in a standard PC (AMD 64) now. I bought a MAC INTEL, and would like to run UBUNTU on it as well, but acording to my experience, the BOOT on the PCs and in the MACs, happens in a diferent way. 

How can I acomplish DUAL boot? do I need the BOOT CAMP from apple?
There are virtual machines now for MACINTELS, will ubuntu run under this?

Thanks

---

### Post by colinhayes on 2006-06-14
[QUOTE=manny_v]I am using UBUNTU in a standard PC (AMD 64) now. I bought a MAC INTEL, and would like to run UBUNTU on it as well, but acording to my experience, the BOOT on the PCs and in the MACs, happens in a diferent way. 

How can I acomplish DUAL boot? do I need the BOOT CAMP from apple?
There are virtual machines now for MACINTELS, will ubuntu run under this?

Thanks[/QUOTE]

you might be best off to run parallel's workstation and install the x86 kernel under that... you wouldn't have to worry about booting into another OS and from what I've seen, the speed is pretty awesome.

---

### Post by slipk487 on 2006-06-14
i think u just need to partiton your hard drave install ubuntu but dont install the grub boot loader but what i dont know is if the x86 ubuntu is install then were does it get the drivers because  is still uses mac hardware thats wat im confused about because im getting a imac soon and i know that when u use boot camp for windows osx burns the drivers for windows so that would been that the x86 probly have the drivers require to run on a imac

---

### Post by slipk487 on 2006-06-14
if any body has any experence with runing ubuntu on a intel imac let me know how u got it to work or how to install it or if ubuntu will even work on a intel mac

---

### Post by omeg on 2006-06-14
I'm wondering about this as well. I'm considering getting an Intel iMac, but I need to be able to run Ubuntu on it, of course. So we could use the x86 version?

Why does the download page not say anything at all about this?

---

### Post by slipk487 on 2006-06-14
it will be a while till im able to get my intel imac so i have time to figure it iut but i think im going to try and get a hold of ubuntu support

---

### Post by manny_v on 2006-06-14
Hi,

i am officially UBUNTUED in MACINTEL, this is the first post from inside Ubuntu running on my MacBook Pro..  Via Virtual Machine .. no dual boot, but WHO NEEDS IT?, this is even better, now I have a fully  funtional MAC (OSX) and perfectly running Ubuntu inside, but better than inside PARALLEL.

GORGEOUS is the only word that comes to my mind..

=========== ADDED ==========

I forgot to tell here that perfomance is great just as colinhayes said...Thanks for the tip.

BTW, tried several VMs, for the price Parallels is the best alternative..

---

### Post by robbyt on 2006-06-15
perfomance is much better when running native!

---

### Post by colinscroggins on 2006-06-15
I was able to install Ubuntu 6.06 in [Parallels]("http://www.parallels.com"), but my internet access and right-click features are not working. Any suggestions?

---

### Post by TheCowardlyLion on 2006-06-15
[QUOTE=manny_v]Hi,

i am officially UBUNTUED in MACINTEL, this is the first post from inside Ubuntu running on my MacBook Pro..  Via Virtual Machine .. no dual boot, but WHO NEEDS IT?, this is even better, now I have a fully  funtional MAC (OSX) and perfectly running Ubuntu inside, but better than inside PARALLEL.

GORGEOUS is the only word that comes to my mind, perfomance is great[/QUOTE]

Which virtual machine are you running?  Have you tried Xgl on it yet?

---

### Post by slipk487 on 2006-06-15
i havent been able to find much about running any version of linux on a macintel

---

### Post by slipk487 on 2006-06-15
i found this  [link]("http://arstechnica.com/news.ars/post/20060125-6045.html") so im guessing they have to adapt the software to be able to run on a intel mac and i wonder if ubuntu will be doing the same thing

---

### Post by entangled on 2006-06-16
I can confirm that Ubuntu 6.06 will install and run on the Intel mac mini; I can't say if this applies to Intel iMac too. 

Basically you have to add two partitions to your hard disk from OSX (will need to resize existing partition), install Boot Camp, install Windows XP (SP2) on one new partition, run Ubuntu 6.06 desktop CD and copy from CD to the other new partition, run lilo, and finally copy the Ubuntu bootloader onto the XP boot partition. Booting needs keyboard to select the right disk every boot time.

The details of doing this are quite lengthy, but available, and there are a few tweaks needed to get login working - and wireless network too.

At the end you have a system that completely works. All the functions I can do in OSX I can also do in Ubuntu; even wpa wireless and bluetooth work.

---

### Post by James_M on 2006-06-16
i think you have to modify the bootloader to work with the EFI BIOS in the new intel macs...don't you?

---

### Post by entangled on 2006-06-16
I didn't modify the lilo file; just ran lilo (slightly awkward because I was running lilo from the live RAM fs, but putting the mbr onto the hard disk partition) and copied the 512 byte mbr as a file over to Windows. The windows boot.ini needed to be edited to offer the mbr file to boot from. Otherwise no different from normal lilo.
Of course this needs refreshing every time the kernel changes.
The other way of booting is via rEFIt, and I found that worked too, but one method is enough for me. I think you can do without Windows if you use rEFIt.

---

### Post by manny_v on 2006-06-16
And I ask myself.......

WHY?

I mean, having OSX "or" windows "or" Ubuntu" when you can have osx "AND" ubuntu "and" windows (do not see a reason for the last one but up to you ;) ) ...

There are several VM for MACINTELs, any would do, but for $50 parallels is great .. now.. this is my setup... 

Macbook pro with 2 GB .. (yes.. that IS the key) ... parallels, 2 VMs.. 
one for windows (allocated 4Gb HD and 768Mb or ram)
...- basically so I can run MsSql 2000 there for my since a customer asked me to put the DBs on it .. 
Other VM for Ubuntu (allocated 8Gb and 768mb ram)
...- This one IS the testing machine, here I am running the apache server, with PHP and freetds to connect to the MsSql server

And the BASIC system in OSX that runs all my other apps.. and is my desktop...

This setup offers you the best a programmer (web programmer that is) can dream of.. each one of the VMs gets its own IP and behaves perfectly.. 

SPEED?.. yes.. when ALL the VMs are working it could get a little slow on the OSX side, but no noticeable on UBUNTU.. windows as MsSql server ONLY runs just fine...

Summary... if you BOUGHT a Macintel, i hope you did because you KNOW what you bought and not because it is a cool toy, it is a LOT MORE than a cool toy, now that I have these setup.. I do not need 3 PCS on my desk anymore.

just my personal experience.. does not mean that it is applicable to anyone else.

Cheers

---

