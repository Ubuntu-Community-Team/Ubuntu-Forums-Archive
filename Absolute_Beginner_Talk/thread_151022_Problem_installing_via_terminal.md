---
title: "Problem installing via terminal"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by L.boothman on 2006-03-27
Hi guys

Having problem when installing via the terminal....=


"louis@ubuntu:~$ cd Desktop
louis@ubuntu:~/Desktop$ sudo dpkg -i mysqlcc_0.9.4-0ubuntu1_i386.deb
Password:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `language-pack-en':
 value for `status' field not allowed in this context
louis@ubuntu:~/Desktop$
"


any one help??

cheers

---

### Post by Xian on 2006-03-27
The /var/lib/dpkg/available is a file that is placed during an apt-get update session and it appears to be corrupt. You might try editing your sources list to use an alternate mirror, do the update again and then try to install the package via Synaptic or similar.

---

### Post by L.boothman on 2006-03-27
Its still not working, i update apt fine however it then still throws me the same error when i try to connect?

---

