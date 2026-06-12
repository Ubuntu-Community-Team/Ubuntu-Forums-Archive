---
title: "Can't install from tar.gz"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Zigon on 2007-08-01
I'm trying to install ndiswrapper-1.47. I can extract it using
```
tar zxvf ndiswrapper-version.tar.gz
```
But everytime I try to "sudo make" I get
```
zigon@zigon-desktop:~/Desktop/ndiswrapper-1.47$ sudo make
make -C driver
make[1]: Entering directory `/home/zigon/Desktop/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/zigon/Desktop/ndiswrapper-1.47/driver'
make: *** [all] Error 2

```

---

### Post by Inxsible on 2007-08-01
Try ```
sudo make install
```

---

### Post by Zigon on 2007-08-01
> **Inxsible said:**
> Try ```
sudo make install
```
Sorry, I should have said that gives me the same thing as "sudo make"

---

### Post by VSpike on 2007-08-01
Try:
sudo apt-get install build-essential
sudo apt-get install linux-headers
make
sudo make install

There may be other dependencies you need to install as well (libraries in other words).  The documentation may give you some pointers, but if not, look at the errors to see what it says it cant find, and try:

aptitude search *xyzlib*

replacing xyzlib with whatever the keyword from the error is.  If you hit a few packages, go for the one with the suffix "-dev".

Good luck!

---

### Post by Zigon on 2007-08-01
Thanks for your reply. I already had the build-essentials so that was all good. But, when I tried 
"sudo apt-get install linux-headers" I got:

```
zigon@zigon-desktop:~$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.20-16-server-bigiron 2.6.20-16.29
  linux-headers-2.6.20-16-server 2.6.20-16.29
  linux-headers-2.6.20-16-lowlatency 2.6.20-16.29
  linux-headers-2.6.20-16-generic 2.6.20-16.29
  linux-headers-2.6.20-16-386 2.6.20-16.29
  linux-headers-2.6.20-16 2.6.20-16.29
  linux-headers-2.6.20-15-server-bigiron 2.6.20-15.27
  linux-headers-2.6.20-15-server 2.6.20-15.27
  linux-headers-2.6.20-15-lowlatency 2.6.20-15.27
  linux-headers-2.6.20-15-generic 2.6.20-15.27
  linux-headers-2.6.20-15-386 2.6.20-15.27
  linux-headers-2.6.20-15 2.6.20-15.27
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

```
:confused:

---

### Post by bodhi.zazen on 2007-08-01
You have to install the headers for your kernel

linux-headers-2.6.20-16-generic

Sometimes it is easier to install the generic headers via synaptic.

Open synaptic and search for linux or linux-headers

You might also want to look at checkinstall, this will make a .deb for you ...

Usually you 

./configure
make  # make does not require sudo
sudo make install

but you can ./configure && make && sudo checkinstall

---

### Post by Zigon on 2007-08-01
In synaptic, it shows that it's already installed.

---

