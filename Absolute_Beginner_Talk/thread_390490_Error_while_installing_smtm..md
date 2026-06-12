---
title: "Error while installing smtm."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-03-22
I have run into a problem while installing smtm thru synaptic. The system prompted me to run " sudo apt-get  install -f ", which I did. The following the result . Coul somebody help me sort this out, please?

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  perl-tk
The following NEW packages will be installed:
  perl-tk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2811kB of archives.
After unpacking 10.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 85043 files and directories currently installed.)
Unpacking perl-tk (from .../perl-tk_1%3a804.027-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/perl-tk_1%3a804.027-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/perl5/auto/Tk/PNG/PNG.so', which is also in package libtk-png-perl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl-tk_1%3a804.027-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1) 

Many thanks in advance,

J

---

### Post by brandoncolorado on 2007-03-22
Maybe relevant?

[https://launchpad.net/ubuntu/+source/perl-tk/+bug/37766](https://launchpad.net/ubuntu/+source/perl-tk/+bug/37766)

---

### Post by Ahmed.Hosny on 2007-03-22
The same error happened with me from a while ..

i was trying to install ClamAV

---

### Post by jagannath on 2007-03-22
> **brandoncolorado said:**
> Maybe relevant?

[https://launchpad.net/ubuntu/+source/perl-tk/+bug/37766](https://launchpad.net/ubuntu/+source/perl-tk/+bug/37766)

Thanks. 
The link sure does lead to the bug responsible for the problem.
So does this mean that I would have to wait for the bug to be fixed? :confused: 

J

---

