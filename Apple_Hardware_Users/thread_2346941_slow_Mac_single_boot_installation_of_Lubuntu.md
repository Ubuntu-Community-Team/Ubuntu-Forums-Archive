---
title: "slow Mac single boot installation of Lubuntu"
date: 2016-12-20
forum: Apple Hardware Users
---

### Post by chimmy3 on 2016-12-20
Greetings,

I have been struggling to get an installation of Lubuntu onto some very old Macs and was finally able to do so my wiping OS X from it completely and making a single boot machine. However, it runs really really really slowly! 

I have about a dozen of these machines and have managed to get Lubuntu on 2 of them with the same result. To give you some perspectives, the machines with 10.4 Tiger (yes, they're that old and there's no possibility to upgrade them as I don't have a 10.5 CD nor do I care to do so) boot up in 25 seconds. The Lubuntu 32-bit single boot machines take 6:20 to get to the login screen. Once started, performance is really bad, too.

To give you some perspective, this is what I'm working with:
- Intel Core 2 Duo 1.83 Ghz
- 512 MB RAM
- Model iMac5,2 (Late 2006 CD)

If you need any other information, I can try to provide it. 

I'll just add I tried to many times to make it dual boot but it simply didn't want to do it. I ended up opting for single boot by reformatting the entire hard disk and installing from the Lubuntu alternate installation CD. It's running, so progress has been made, but it be at all useful it needs to run at a reasonable speed, ideally as well as when it's running OS 10.4.

---

### Post by jeremy31 on 2016-12-20
*Thread moved to **Apple Hardware Users**.*

Welcome to the forums

---

### Post by abtabt on 2016-12-20
try to
install htop and gnome-disk-utility  
and  if you can see whats slow down ,swap etc 
gnome-disk-utility you can se if hdd is damage etc

version lubuntu ???

---

### Post by mörgæs on 2016-12-21
The 512 MB of memory is of course a limitation. Let's see if there are more.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

