---
title: "[SOLVED] libdvdcss?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by irishgoth8822 on 2008-03-01
i am trying to get my movie player (any of them!) to work with my dvds, and when i try to install libdvdcss via terminal, i keep getting this message:

```
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

i have also tried adding the mediabuntu line to my apt. sources list...

what should i do?

---

### Post by deadmnky on 2008-03-01
you could try to reinstall the medibuntu repo. if that does not work i knwo sourceforge or the debian website have them as tar.gz or even deb packages you could try and build it up from source

---

### Post by wolfen69 on 2008-03-01
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo apt-get install libdvdcss2
```

---

### Post by irishgoth8822 on 2008-03-01
thank you thank you thank you!

that worked perfectly! :)

---

### Post by cebe11 on 2008-03-01
I have same problem but on feisty.  I followed these instructions:

```
For Ubuntu Feisty Fawn Users

deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

Now you need to copy the key using the following command

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

Update the source list using the following command

sudo apt-get update

Install Codecs using the following command

sudo apt-get install w32codecs libdvdcss2
```

When I do sudo apt get update, I get the following errors:

```
Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/feisty/dists/free/non-free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 302 Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
And then when I do sudo apt-get install libdvdcss2 win32codecs I get


```
 sudo apt-get install w32codecs libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate



```

This is the second time around installing libdvdcss2 and both times it gave me problems, I can't remember how I solved it the first time!!!
Help appreciated!!

---

### Post by irishgoth8822 on 2008-03-01
thats actually exactly what was happening to me when i tried to follow instructions along those same lines.

i dont know, but perhaps you could try doing what wolfen69 suggested but changing anywhere that says 'dapper' to feisty.

---

