---
title: "linux-header help"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Electrical_shock on 2007-10-04
I'm trying to complete this How to: [http://ubuntuforums.org/showthread.php?t=262465&highlight=wpnt511](http://ubuntuforums.org/showthread.php?t=262465&highlight=wpnt511)


My problem is when I try to execute "sudo apt-get install linux-headers-$(uname -r)" I get:  

sudo aptitude install linux-headers-$(uname -r)
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I tried installing the linux-headers from Synaptic I get:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-29_2.6.15-29.58_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-29_2.6.15-29.58_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-29-386_2.6.15-29.58_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-29-386_2.6.15-29.58_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]



I'm using Ubuntu 6.06 and uname -r returns 2.6.15-29-386.  Any ideas?

---

### Post by Pumalite on 2007-10-04
Close Synaptic while you are using apt-get.

---

### Post by kevdog on 2007-10-04
the command is the following:

sudo aptitude install linux-headers-`uname -r`

Note those are backticks and not quotes.

---

### Post by Electrical_shock on 2007-10-04
Tried the command:

sudo aptitude install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  linux-headers-2.6.15-29
The following NEW packages will be installed:
  linux-headers-2.6.15-29 linux-headers-2.6.15-29-386
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7765kB of archives. After unpacking 79.6MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-29 2.6.15-29.58
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-29-386 2.6.15-29.58
  404 Not Found [IP: 91.189.88.37 80]


Error finding the headers, same as when trying to install them from synaptic.  How do I work around this?

---

### Post by Pumalite on 2007-10-04
Server temporarily down probably. Try later. Or bad connection. Ping IP

---

### Post by kevdog on 2007-10-05
As above the site is temporarily down -- try again later -- sorry (or if you have the installation cd another alternative):

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`

Not a bad solution if you have the disk available and dont want to wait.
Make sure you have the build-essential package also installed if you are doing compiling.  This is also on the CD if you cant get it off the net.

---

### Post by macogw on 2007-10-05
> **kevdog said:**
> the command is the following:

sudo aptitude install linux-headers-`uname -r`

Note those are backticks and not quotes.

$() and backticks do the same thing.  The nice thing about $() is that you can have backticks returning something to a larger command inside $() which returns its output to the overall command.  In other words: backticks can't nest in themselves, but they can in $()

---

### Post by Electrical_shock on 2007-10-06
Thanks.  I loaded the headers off the cd and I'm now typing this over the wireless connection.

---

