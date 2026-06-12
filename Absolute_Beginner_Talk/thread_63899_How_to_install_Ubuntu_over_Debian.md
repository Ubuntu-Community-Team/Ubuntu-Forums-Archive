---
title: "How to install Ubuntu over Debian?"
date: 2005-09-09
forum: Absolute Beginner Talk
---

### Post by MacBaron on 2005-09-09
Debute:

I have an old PII laptop on which I installed the Debian netinstall cd. Now I dont want that anymore, since I never got it to work, and got the Ubuntu iso

[http://www.ubuntu.com/download/](http://www.ubuntu.com/download/)

and tried to install that. But everytime I try to boot from the Ubuntu cd I get that Debian anyway. Everytime I change boot drive in PhoenixBIOS but I still boot in Debian.

All I want is a system that needs little or no maintenance that I can use for websurfing.

I know absolutely nothing about Linux, nothing about Windows but I do pretty well in MacOS9-X.

---

### Post by Kvark on 2005-09-09
Sounds like your CD is not bootable. What program did you use and exactly how did you burn it? Is there only one file or several directories and files on the CD?

It's very important that you use the "burn from image" (or something similar, depending on program) option.


Another possible problem is a corrupted download. Check the checksum of the iso file, in linux just type "md5sum filename.iso" into a terminal, in windows you need some special program to check it. Then compare the random letters and numbers the command gives you with the md5 checksum listed on the download mirrors, if it matches then your download is ok.

---

### Post by MacBaron on 2005-09-09
[QUOTE=Kvark]Sounds like your CD is not bootable. What program did you use and exactly how did you burn it? Is there only one file or several directories and files on the CD?

It's very important that you use the "burn from image" (or something similar, depending on program) option.[/QUOTE]
I used Disk utility in Mac OSX 10.4. The cd contains these (visible) folders:

README.diskdefines (unknown format)
install (folder)
preseed (folder)
isolinux (folder)
ubuntu (shortcut to the very cd)
dists (folder)
pool (folder)
md5sum.txt (text file)
doc (folder)
pics (folder)

> Another possible problem is a corrupted download. Check the checksum of the iso file, in linux just type "md5sum filename.iso" into a terminal, in windows you need some special program to check it. Then compare the random letters and numbers the command gives you with the md5 checksum listed on the download mirrors, if it matches then your download is ok.
I can't find the sum of the iso..

---

### Post by MacBaron on 2005-09-09
[QUOTE=MacBaron]I used Disk utility in Mac OSX 10.4. The cd contains these (visible) folders:

README.diskdefines (unknown format)
install (folder)
preseed (folder)
isolinux (folder)
ubuntu (shortcut to the very cd)
dists (folder)
pool (folder)
md5sum.txt (text file)
doc (folder)
pics (folder)


I can't find the sum of the iso..[/QUOTE]
 Now I have tried the 5.04 instead of the 5.10 I accidentally got the last time. But it still doesn't boot. :mad:

---

### Post by MacBaron on 2005-09-09
[QUOTE=MacBaron]Now I have tried the 5.04 instead of the 5.10 I accidentally got the last time. But it still doesn't boot. :mad:[/QUOTE]
 all calls are off! It was just me who thought I knew my way around Phoenix BIOS when I didn't. 8)

---

