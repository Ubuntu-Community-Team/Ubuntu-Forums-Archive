---
title: "Macbook 7,1 single vs dual boot?"
date: 2011-03-10
forum: Apple Hardware Users
---

### Post by hussainq86 on 2011-03-10
Hello there! 

I have a Macbook 7,1 (the white one)
2.4GHz Intel Core 2 Duo
2GB DDR3 memory
250GB hard drive

I'd like to install Ubuntu on it because I really love the way Ubuntu is developing and becoming much more user friendly. My use will mainly be for browsing, working with wordprocessors and maybe downloading series from torrents. 

My question is, should I dual boot or single boot? My personal preference is to single-boot, I just like the idea of having one OS running on the machine. What are the cons of doing that? Also, If I want to dual boot just to keep the firmware updates (are they really very crucial?)  how much space should I designate for Ubuntu and how much for Mac OS?

---

### Post by Colin Rovis on 2011-03-10
You should do a Dual-Boot.

1) Have Mac OS X 10.6.6 installed
2) Bootcamp: Reserve 30 GB for "Windows" (Mac does not know other OSes than itsself and Windows)
3) Boot with Ubuntu and install Ubuntu on disk0s3 (i guess, this will be the partition bootcamp will create)
4) Important: Dont let Ubuntu install grub on MBR, but on /dev/sda3 (the partition bootcamp created)
5) Install rEFIt
6) Enjoy, but with restrictions: Your CPU-Cores will not be recognized due to the fact that the Mac uses efi instead of bios.

---

### Post by _mario_ on 2011-03-10
> **hussainq86 said:**
> 
My question is, should I dual boot or single boot? My personal preference is to single-boot, I just like the idea of having one OS running on the machine. What are the cons of doing that? 


1. As you said: firmware installation. Not that often necessary, but if it fixes something important?
2. No Mac OS anymore. Seriously, sometimes I managed to screw up my Ubuntu installation, and was very happy to have OS X around. On the other hand, having no OS X anymore can also be a pro.

> **hussainq86 said:**
> 
Also, If I want to dual boot just to keep the firmware updates (are they really very crucial?)  how much space should I designate for Ubuntu and how much for Mac OS?

If you reinstall OS X, you can disable pretty much everything you don't need: printer drivers (saves ~4GB), language support (~4GB), and all applications shipped by default (with the exception of iTunes). The final installation takes approximately 8GB of disk space, so a 10GB partition might suffice. Personally, I used 20GB for OS X where - after installing Xcode to get MacPorts to work and some MacPorts applications - 5.7GB are still free.

ciao,
Mario

---

