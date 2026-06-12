---
title: "installation trouble"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by p_a_church on 2006-05-17
Hi,
I am completely new to linux-ubuntu.
Have followed all the instructions but the install fails to load the base system with the following errors.

couldnt download zlib1g

unable to install initrd-tools.

It then fails to copy the remaining packages to the hard disk.

I have tried re-burning, loading server only, minimal installs without success.

Any help appreciated.

Thanks.

---

### Post by sYs^ on 2006-05-17
Try re-downloading, might it helps :>

---

### Post by xXx 0wn3d xXx on 2006-05-17
[QUOTE=p_a_church]Hi,
I am completely new to linux-ubuntu.
Have followed all the instructions but the install fails to load the base system with the following errors.

couldnt download zlib1g

unable to install initrd-tools.

It then fails to copy the remaining packages to the hard disk.

I have tried re-burning, loading server only, minimal installs without success.

Any help appreciated.

Thanks.[/QUOTE]
At what speed did you burn the cd ? The cd should be burned at 4x or lower. Try doing a server install and then typing the following from terminal:

> sudo apt-get install ubuntu-desktop

This will give you a GUI and give you a fully functional system.

---

### Post by p_a_church on 2006-05-18
Thanks for your replies.
I have already tried the server install it gave the same error messages. I have tried various installs from the help file and from wiki.ubuntu. 
I burnt the first copy at 4x and the second copy at 1x !! . Both fail with exactly the same problem at the same time. Unfortunately it's the 'install base system' step that fails. 
I was hoping not to have to re-download the iso :)

Any more idea's please? My last iso download took 7 hours (yes, seven!!) 
Thanks.

---

### Post by skinnygmg on 2006-05-18
Did you md5sum the download?

---

### Post by p_a_church on 2006-05-18
Yes. I followed the instructions for verifying using the md5 hash checksum and it verirfied fine.

---

