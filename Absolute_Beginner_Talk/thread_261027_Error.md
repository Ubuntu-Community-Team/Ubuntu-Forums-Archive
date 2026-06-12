---
title: "Error"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by mattfender on 2006-09-19
Can someone help me fix this error please

Could not download all repository indexes.....

cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/dists/dapper/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs



Thanks

---

### Post by bluefrog on 2006-09-20
have you used apt-cdrom command line as suggested?

James

---

### Post by Najand on 2006-09-20
Try to edit your /etc/apt/sources.list and remove all lines starting with 
"deb cdrom"
and then add your ubuntu CD using "sudo apt-cdrom" command to make your Ubuntu CD recognized by your package manager system: apt.

---

### Post by mattfender on 2006-09-20
The only thing I have done was try to install R by using a code give on here by someone, then I marked a few packages for installation, that I thought had to do with that program because I could not find the program anywhere on my computer. 
I tried getting into my list as I have done before, but I must be doing something wrong. How is it you get in there again?

---

