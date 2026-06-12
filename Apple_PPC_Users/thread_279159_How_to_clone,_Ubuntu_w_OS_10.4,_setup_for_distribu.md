---
title: "How to clone, Ubuntu w/ OS 10.4, setup for distribution"
date: 2006-10-17
forum: Apple PPC Users
---

### Post by nomados on 2006-10-17
I have the ulimate (everything I need) setup. Two main partitions Dapper (Ubuntu) and OSX.4. MOL is setup along with its networking etc. How can I make a clone of this drive which includes both partitions (bit for bit) so that I can pop it into a like machine and get going?

I've used G4L on 386 linux distros and it has worked great, but whenever I try to use G4L on the ppc drive, the copy goes as expected, but the end result will not boot into either partition giving me the folder icon.

My Issue probably has something with the Apple Partition Map, but am unsure. Is there anything like G4L or another way to use G4L to make a clone of this ppc system? Apple supported apps only see the HFS partitions so I cannot make a clone using Disk Utility.

tia,
n

---

### Post by stmiller on 2006-10-17
This might be sticky to find an all-in-one solution, as all the os x apps that do this do not read ext3. A Linux solution may be out there (the newest kernels can read/write HFS+), but I would be unsure if it would copy the OS X partition intact the way OS X wants it.

You could possibly use a combination of the Carbon Copy for the OS X side and another program for the Linux side. Then restore each on their own.

---

### Post by nomados on 2006-10-18
I got it figured out.

Stuck the disks onto an IDE chain on a X86 machine, booted up from cd rescue disk and used dd to dupe the disks. 

%  dd if=/dev/hda of=/dev/hdc ; hda master  hdc destination

I also figured out that my interpretation of the jumper markings on the disks I was using were causing boot up problems, so I removed the jumpers from them totally. Disco!

Back in business.

---

### Post by nitinbhamare on 2007-11-14
Hi,

I have installed Ubuntu Linux 6.0.6 LTS and few softwares on my PC. Now I want to make the ghost image of my Hard Disk and then make a bootable CD.

Using this botable CD, I will be able to install the same OS, software etc within few mnutes.

How to do this? Is there any utility available? Please send me.

regards,

Nitin.

---

### Post by oswaldkelso on 2007-11-16
Hers how to do the osx bit scroll to the bottom of the post

[http://forums.debian.net/viewtopic.php?t=18193]("http://forums.debian.net/viewtopic.php?t=18193")

---

