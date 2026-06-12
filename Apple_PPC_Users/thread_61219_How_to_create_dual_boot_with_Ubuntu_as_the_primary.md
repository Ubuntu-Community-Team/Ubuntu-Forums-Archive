---
title: "How to create dual boot with Ubuntu as the primary OS?"
date: 2005-08-30
forum: Apple PPC Users
---

### Post by Aerolite on 2005-08-30
My system has Ubuntu only...no Mac OS, and I'm wondering if there are any directions as to how to make it dual boot with OS X and/or OS 9.1.  How would I go about partitioning?

---

### Post by ubuntme on 2005-08-30
I'm not sure if this is going to be any help since I know nothing of mac OS, but when creating a dual boot windows / linux maching you always want to put windows on first as windows does nasty things to the master boot record...  not sure if this is the case with mac OS..

---

### Post by calum on 2005-08-31
[QUOTE=Aerolite]My system has Ubuntu only...no Mac OS, and I'm wondering if there are any directions as to how to make it dual boot with OS X and/or OS 9.1.  How would I go about partitioning?[/QUOTE]

Both Ubuntu and OSX have options to create partitions during the install.  I don't know if it matters which one you install first, but I installed OSX first on my dual-boot Powerbook, creating a second partition in the process.  When you then go back and install Ubuntu, it will let you choose which partition to install it on.

I forget which OS will boot by default without further tinkering, but it's certainly possible to choose by editing Ubuntu's /etc/yaboot.conf file.  There's also a GUI for doing this, under System->Administration on Ubuntu IIRC.

---

### Post by nickfull on 2005-09-01
[QUOTE=calum]Both Ubuntu and OSX have options to create partitions during the install.  I don't know if it matters which one you install first, but I installed OSX first on my dual-boot Powerbook, creating a second partition in the process.  When you then go back and install Ubuntu, it will let you choose which partition to install it on.

I forget which OS will boot by default without further tinkering, but it's certainly possible to choose by editing Ubuntu's /etc/yaboot.conf file.  There's also a GUI for doing this, under System->Administration on Ubuntu IIRC.[/QUOTE]

If you want a poly-boot set up with OSX / 9 / Ubuntu the easiest way is to start from scratch and install OSX first, making separate partitions for OSX / OS9 / Ubuntu (using HFS+ formated partitions and reformating the ubuntu partition later during installation).  

I don't know if it's possible to install Ubuntu on a machine that is already running OSX? Re-partitioning the drive will still leave you the problem of OSX deblessing the bootload setup, which is why OSX should go on the machine first. Should boot into ubuntu by default, yaboot giving the option also to select 'x' (OSX) or 'm' (OS9) or 'c' (CD-ROM). There are HOWTOs out there, have a look on google/ubuntu wiki. A debian/osx dual boot howto is also pertinant.

---

### Post by ninotob on 2005-09-01
Just want to add in my experiences.  I have OSX and Ubuntu running fine.  I installed OSX 10.3 first and then Ubuntu.  This was on an Clamshell iBook  

However, the first time I installed these, I had OSX make two HFS+ partitions on my HD.  I installed OSX on the first, and Ubuntu on the second -- for some reason, this borked OSX and I couldn't boot it.  At that time I didn't look into what had happened, I just dithched my linux install and reinstalled OSX (I was lending the laptop to someone w/o linux experience).

The other day, I decided to try again.  So I started with OSX and had it partition the drive into two, but instead of formating the future linux partition, I had it leave it unformated.  When I installed Ubuntu, I chose the automatic "use empty space" partitioning scheme.  When it was done, everything worked as it was supposed to -- the bootloader menu was automagically generated perfectly and both OS's boot up fine.  Also, the default bootloader behavior is to load linux.

So my advice, load OSX first, but don't format the second partition when doing a format/install with OSX.

---

