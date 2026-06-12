---
title: "Linux-source error"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by WKnew on 2007-02-17
Attempting to add Truecrypt 4.2a. Following how-to dowload Trurecrypt, apt get build-essential, enter the following command:

cd /usr/src/
sudo bunzip2 linux-source-2.6.17.tar.bz2

Get this error:

bunzip2: Can't open input file linux-source-2.6.17.tar.bz2: No such file or directory.

I looked for linux-source-2.6.17.tar.bz2 and can't find it. Does the above error mean it has been deleted or missing?

---

### Post by ola on 2007-02-17
Hi! From what I understand that means that you haven't downloaded the Linux kernel source yet. I assume that howto you are reading needs to have the source for the Linux kernel as well.

The Linux Kernel page is located at [http://www.kernel.org/](http://www.kernel.org/) and if you prefer you can download the kernel source as a deb-packade using apt (something like sudo apt-get install linux-source-2.6.17).

Good luck!

---

### Post by orb9220 on 2007-02-19
also the source file has a .bin on the end which is the problem. Just rename and remove the .bin off the source ball.

[http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/)

---

