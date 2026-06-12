---
title: "Everything is so slow on Ubunutu 16.04"
date: 2017-08-06
forum: Apple Hardware Users
---

### Post by ndelasoul on 2017-08-06
Everything I do is slow. Even surfing the internet is slow when I have a 40mb connection. The only OS I have on here is Ubuntu 16.04 LTS

Macbook Pro mid-2012
[https://support.apple.com/kb/sp649?locale=en_US](https://support.apple.com/kb/sp649?locale=en_US)

_Ubuntu Overview_
Memory     7.7 GiB
Processor  Intel Core i5--3210M CPU @ 2.50 GHZ x 4
Graphics    Intel Ivybridge Mobile
OS Type    64-bit
Disk          483.7 GB

Any help is much appreciated. Thank you.

---

### Post by QIII on 2017-08-06
Moved to Apple Hardware Users for a better fit.

Cheers!

---

### Post by ndelasoul on 2017-08-06
I saw a link on here for oibaf graphics driver. I installed it on my macbook and it made a huge difference in performance. I tried to update the driver, but that wasn't successful.


tiger@ether:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release [1,189 B]           
Get:4 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg [819 B]         
Get:6 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Err:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release.gpg                 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6494C6D6997C215E
Get:7 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [304 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:9 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) xenial InRelease [17.6 kB]
Get:10 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [207 kB]
Get:11 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [165 kB]
Get:12 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [215 kB]
Get:13 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:14 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:15 [http://tw.archive.ubuntu.com/ubuntu](http://tw.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,688 B]
Get:16 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) xenial/main amd64 Packages [17.2 kB]
Get:17 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) xenial/main i386 Packages [17.2 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [59.2 kB]
Get:19 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) xenial/main Translation-en [9,352 B]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [49.6 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [43.0 kB]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [58.8 kB]
Fetched 1,484 kB in 4s (344 kB/s)                                      
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6494C6D6997C215E
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6494C6D6997C215E
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

