---
title: "md5sum?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by noobbutnotboob on 2007-06-22
Dowloading some unshield from packages.ubuntu.com and it gives me a box from where I have to choose the correct version. This is based on md5sum which is just a string of numbers, of course. The question is, how do I find out what the md5sum is on my laptop? 

Thanks in advance... :)

---

### Post by logos34 on 2007-06-22
The md5sums are to check the integrity of the downloaded files.  You do this via the terminal:

cd /directory/containing/downloadedfiles
md5sum <packagename>

It will print out a string.  just compare it to the sum listed on the webpage.  They should match exactly.

---

### Post by Najand on 2007-06-22
Well... we don't usually download from packages.ubuntu.com as they are all packages included in the repositories. If you want to use those packages it is extremely recommended to use apt-get to download and install such packages.

---

### Post by noobbutnotboob on 2007-06-22
ok another dumb question... I've used apt-get before but not sure about using it 'dry' without some text guiding me. The packages I want are unshield and libunshield, which are given in some directions to get a wireless card to work (the actuall issue under another thread). Given what little I know, I tried 'apt-get -q libunshield' and get invalid operation libunshield. So does this mean that that package isn't installed in my repositories, or that I'm running the apt-get incorrectly? Plus I've got no internet connection at all (that's what I'm trying to fix, while accessing the forums on my desktop). Ideas?

---

### Post by logos34 on 2007-06-23
**dpkg -l**			

or

**dpkg --get-selections**		

will list all deb packages installed on your system.  

You need internet connection to run **apt-get** (the repos in your /etc/apt/sources.list are just the places where you download packages from).  

**sudo apt-get install <packagename>**

You can download the packages you mentioned [here (Feisty)]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unshield&searchon=names&subword=1&version=feisty&release=all").  Copy to usb stick or floppy, transfer them to /home/user diretory on your laptop, check the md5sums, and install:

**sudo dpkg -i <packagename>**

Here's the info with md5sums from apt for unshield, libunshield0 and libunshield-dev:
> 
xxxx@xxxx-desktop:~$ apt-cache search unshield
libunshield-dev - development files for libunshield
libunshield0 - library to extracts CAB files from InstallShield installers
unshield - extracts CAB files from InstallShield installers

xxxx@xxxx-desktop:~$ apt-cache show libunshield-dev
Package: libunshield-dev
Priority: optional
Section: universe/libdevel
Installed-Size: 84
Maintainer: Volker Christian <voc@debian.org>
Architecture: i386
Source: unshield
Version: 0.5-3
Depends: libunshield0 (= 0.5-3)
Filename: pool/universe/u/unshield/libunshield-dev_0.5-3_i386.deb
Size: 14438
MD5sum: 4b0a1198a054ebee95b1ab16d5aa7553
SHA1: c1f558c7cd3b61f3019d3d53e90e3ed03651bdf9
SHA256: 69efae534501eb6a4f8aa36eb097b90fc98384d120d29be78a91f16d83b32d6b
Description: development files for libunshield
 This are libraries to create applications extracting CAB files from
 InstllShield installers used to be installed on Windows CE devices or
 Windows desktop machines.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

xxxx@xxxx-desktop:~$ apt-cache show unshield
Package: unshield
Priority: optional
Section: universe/utils
Installed-Size: 60
Maintainer: Volker Christian <voc@debian.org>
Architecture: i386
Version: 0.5-3
Depends: libc6 (>= 2.3.4-1), libunshield0 (>= 0.5), zlib1g (>= 1:1.2.1)
Filename: pool/universe/u/unshield/unshield_0.5-3_i386.deb
Size: 8124
MD5sum: 1b607f4f5287941faf271cafa564fd58
SHA1: 9748986ce51bab723fde7e8b101586cbb6e9b7ed
SHA256: 8bc26f8a466bc372c1004af572a0b96f9c5a25e444958ad6fabb974225c4330e
Description: extracts CAB files from InstallShield installers
 This software extracts CAB files from InstllShield installers
 used to be installed on Windows CE devices or Windows desktop
 machines.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

xxxx@xxxx-desktop:~$ apt-cache show libunshield0
Package: libunshield0
Priority: optional
Section: universe/libs
Installed-Size: 72
Maintainer: Volker Christian <voc@debian.org>
Architecture: i386
Source: unshield
Version: 0.5-3
Replaces: libunshield
Depends: libc6 (>= 2.3.4-1), zlib1g (>= 1:1.2.1)
Conflicts: libunshield, liborange
Filename: pool/universe/u/unshield/libunshield0_0.5-3_i386.deb
Size: 13190
MD5sum: 4f52891a95bed2f458e3486b789066b9
SHA1: fdfe26e7106c63db5f4af5d9d27457a5dd41f936
SHA256: 04a2b6966f67a5ff80c6434031a58cc9d13a89df11c7b35ed7d68afda9bd4e47
Description: library to extracts CAB files from InstallShield installers
 This are libraries to create applications extracting CAB files from
 InstllShield installers used to be installed on Windows CE devices or
 Windows desktop machines.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Hope that helps you get your wireless working!

---

### Post by noobbutnotboob on 2007-06-23
logos34! You are awesome! thank you so much for that info!

One thing I have come to realize in all this: windows has made me stupid. It's removed me so much from the actual doing of things (after all, just 'click here') that I no longer know how to understand how things work (much less do things). ](*,)

---

### Post by bodhi.zazen on 2007-06-23
> **noobbutnotboob said:**
> Dowloading some unshield from packages.ubuntu.com and it gives me a box from where I have to choose the correct version. This is based on md5sum which is just a string of numbers, of course. The question is, how do I find out what the md5sum is on my laptop? 

Thanks in advance... :)

I worte a quick tutorial on md5 and sha1 sums here 

[http://ubuntuforums.org/showthread.php?t=290339](http://ubuntuforums.org/showthread.php?t=290339)

You can check the integrity of the file with :

```
md5sum -c file.md5
```

Where "file.md5" is a properly formatted md5sum file (usually just download the md5 or sha1 from the download site).

check it out :

> md5:
bodhi@Arch:~$md5sum -c groups.md5sum
**[color=navy]groups: OK**[/color]
bodhi@Arch:~$

sha1:
bodhi@Arch:~$sha1sum -c groups.sha1
**[color=navy]groups: OK**[/color]
bodhi@Arch:~$

See the "OK" That means all is good :)

---

