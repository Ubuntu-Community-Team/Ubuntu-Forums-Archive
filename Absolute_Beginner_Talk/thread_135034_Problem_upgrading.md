---
title: "Problem upgrading"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by xerob on 2006-02-23
When i run apt-get dist-upgrade i get the following error message:
(Yes i did run apt-get update before dist-upgrade)

Seems the 'iproute' package is messing me up, i tried to remove it
but that failed aswell. Is there a file that i can edit and give iproute
the missing newline ? 


Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnupg libgnutls11 libtasn1-2 linux-image-2.6.12-10-386 openssh-client unzip
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.1MB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gnupg_1.4.1-1ubuntu1.1_i386.deb (--unpack):
 files list file for package `iproute' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/gnupg_1.4.1-1ubuntu1.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heimo on 2006-02-23
My first attempt in solving these kind of problems is to remove the package if it doesn't force to remove half of my other packages (in this case I think it shouldn't be a problem).
```
sudo apt-get remove iproute
```

Then move away couple dpkg files:
```
mv /var/lib/dpkg/info/iproute.* /tmp
```

And then reinstall the package:
```
sudo apt-get install iproute
```

Does it work? If not, you could try to edit  /var/lib/dpkg/info/iproute.list and add that newline.

---

### Post by xerob on 2006-02-23
Thanks for the help, editing the file and making a newline did the trick :D 

// Eric

---

