---
title: "gcc compiler"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by sazdo on 2006-09-04
Hallo to everybody,

I&#8217;m trying to install gcc compiler. 
After I wrote  apt-get install gcc. In the beginning everything is  OK and in the middle I get that the following packages cannot be authenticated. It seems that I don&#8217;t have this packages. 
I was not connected to the internet when I was doing this. Maybe this is the problem. Maybe I need some CD. 

Please see what I got after the  apt-get install gcc

Reading package lists... Done
Building dependency tree... Done
The following  extra packages  will be installed:
binutils cpp cpp-4.0 gcc-4.0
Suggested packages:
binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9
libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1
Recommended packages:
libc6-dev libc-dev libmudflap0-dev
The following NEW packages will be installed:
binults cpp cpp-4.0 gcc gcc-4.0
0 upgraded, 5 newly instaled, 0 to remove and 0 not upgraded.
Need to get 0B/4043kB of archives.
After unpacking 12.5 MB of additional disk space  will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages  cannot be authenticated!
binults cpp cpp-4.0 gcc gcc-4.0
Install  these packages without verification [Y/n]? y
Err file:  breezy/main binults 2.16.1-2ubuntu6
File not found
Err file:  breezy/main cpp-4.0 4.0.1-4ubuntu9
File not found
Err file:  breezy/main cpp-4.4 0.1.-3
File not found
Err file:  breezy/main gcc-4.0 4.0.1-4ubuntu9
File not found
Err file:  breezy/main gcc-4.4 0.1.-3
File not found
Failed to fetch file:///cdrom/pool/main/b/binutils/binutls_2.16.1-2ubuntu6-i386.deb
File not found
Failed to fetch file:///cdrom/pool/main/g/gcc-4.0/cpp-4.0_4.0.1-4ubuntu9_i386.deb
File not found
Failed to fetch file:///cdrom/pool/main/g/gcc-defaults/cpp-4.0.1-3_i386.deb
File not found
Failed to fetch file:///cdrom/pool/main/g/gcc-4.0/gcc-4.0_4.0.1-4ubuntu9_i386.deb
File not found
Failed to fetch file:///cdrom/pool/main/g/gcc-defaults/cpp-4.0.1-3_i386.deb
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multivrese_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: You may want to run apt-get update to correct this problems
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I also tried to update. Maybe the problem was that I was not connected to the internet. Maybe I need some CD with packages. This is what I got:

apt-get update

Ign file: breezy Release.gpd
Ign file: breezy Release
Ign file: breezy/ main Packages
Ign file: breezy/ restricted Packages
Ign file: breezy/ main Packages
      File not found
Err file: breezy/ restricted Packages
      File not found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpd
   Temporary failure resolving &#8216;archive.ubuntu.com&#8217;
Fail to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg) Temporary failure
resolving &#8216;archive.ubuntu.com&#8217;
Failed to fetch file:///cdrom/dists/breezy/main/binary-i386/Packages.gz File not found
Failed to fetch file:///cdrom/dists/breezy/restricted/binary-i386/Packages.gz File not found
Reading package lists ... Done
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: Couldn&#8217;t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multivrese_binary-i386_Packages) &#8211; stat (2 No such file or directory)
W: You may want to run apt-get update to correct this problems
E: Some index files failed to download, they have been ignored, or old ones used instead

I downloaded the packages from the Ubuntu web site. Now can I put them on a CD to update. Is this possible or not.
Please if someone knows what is the solution to help me

---

### Post by taurus on 2006-09-04
Why do you have to post the same problem TWICE!!!  :rolleyes:

---

