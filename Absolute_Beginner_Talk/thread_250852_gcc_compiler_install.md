---
title: "gcc compiler install"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by sazdo on 2006-09-04
Hallo to everybody,

I’m trying to install gcc compiler. 
After I wrote  apt-get install gcc. In the beginning everything is  OK and in the middle I get that the following packages cannot be authenticated. It seems that I don’t have this packages. 
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
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multivrese_binary-i386_Packages) – stat (2 No such file or directory)
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
   Temporary failure resolving ‘archive.ubuntu.com’
Fail to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg) Temporary failure
resolving ‘archive.ubuntu.com’
Failed to fetch file:///cdrom/dists/breezy/main/binary-i386/Packages.gz File not found
Failed to fetch file:///cdrom/dists/breezy/restricted/binary-i386/Packages.gz File not found
Reading package lists ... Done
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) – stat (2 No such file or directory)
W: Couldn’t stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multivrese_binary-i386_Packages) – stat (2 No such file or directory)
W: You may want to run apt-get update to correct this problems
E: Some index files failed to download, they have been ignored, or old ones used instead

I have downloaded the packages from the Ubuntu web site. Now can I put them on a CD to update. Is this possible or not.

Please if someone knows what is the solution to help me.

---

### Post by bluefrog on 2006-09-04
internet seems to be the key in that case, not everything being on the cd

James

---

### Post by taurus on 2006-09-04
Instead of install gcc, I recommand you install build-essential since it's more complete.

```

sudo aptitude update
(and if you get the same error message that you got, run "sudo aptitude update" again...)
sudo aptitude install build-essential

```

---

### Post by sazdo on 2006-09-04
I tried to connect to the internet. Acctualy i did not succed because my modem was not recognoized by ubuntu. Can you tell me how to connect to the internet. I dont have possibilities with ADSL or something faster only dial up. Can this do the job for me. 
How to I do this

---

### Post by sazdo on 2006-09-04
I tried with sudo aptitude install build-essential but now i get that aptitude: command not found 
Really I dont understand

---

### Post by Bagnaj97 on 2006-09-04
try ```
sudo apt-get install build-essential
```

---

### Post by sazdo on 2006-09-04
I tried everything. I think that the solution  will be comnecting to the internet. Can some one tell me how to connect to the internet with modem.

I tried before but I had problem because Ubuntu did not recognized the modem on my laptop.

---

### Post by catlett on 2006-09-04
Yes that is exactly the problem. Apt-get, aptitude amd synaptic package manager all use online repositories to get the applications. If you cannot acccesss the internet neither can they.

If you have the installation cd, put iot in and run sudo apt-get install buil-essentisl. Build essential is on the cd but it doesn't get installed.

Your best bet with the modem is to start a new thread so people with modem experience will notice the title. Right now peole think you are having compiler issues.

---

### Post by sazdo on 2006-09-04
Thanks, you are right. I tried to put the instalation CD but I was not able to start the CD. When i tried to open it, Ubuntu sad that it can't mount the CD. 
What should I do now.

---

### Post by catlett on 2006-09-04
Wow your having alot of trouble with your system. For now try putting the cd in and issuing this command ```
sudo mount /media/cdrom0/ -o unhide
``` If that works it won't be permanent. That will only manually mount it for this session. You would unmountg the cd with this command```
 sudo umount /media/cdrom0/
```
The file /etc/fstab tells the computer hwta to mount. Post the result of this command ```
cat /etc/fstab
```

---

### Post by sazdo on 2006-09-04
Sorry for the delay. I'm swithcing the laptop from Windows to send the message and Ubuntu to try the things that you tell me. 
I tried the code and again the CD was not mounted. 
I'm sure that the CDrom is not a problem because in Windows is working fine. What  is the problem now I dont really undersatand.

---

### Post by sazdo on 2006-09-04
I put the instalation CD and I manage to isntall the bulad essential. From what can I understand the gcc compiler together with other programs is unpacked somewhere?????
Where I can find now the gcc compiler in order to start configuring and make the compiler.
Maybe there is some autoconfiguraion way.I dont know. I will stop guessing here. 

Can someone tell me what is next after the sudo apt-get install build-essential. Where is the gcc compiler and how can I install him.

---

### Post by sazdo on 2006-09-04
Sorry for the mistakesin the last post. Can someone help me to install the gcc. I looking for the package in the tree but I was not able to found the packages.

---

### Post by sazdo on 2006-09-04
The gcc compiler is instaled. Thanks you guys for your help. I appreciate a lot. Stay in touch.

---

### Post by catlett on 2006-09-04
Sorry to leave you hanging. My sister had her baby and I went to the hospital. I guess the compiler worked out. If build essential installed, you can just start using ```
./configure 
``````
make 
```and ```
sudo make install
``` For compiling.
What happened with the cd drive? Did it mount? If you are still having issues, what is the output of ```
cat /etc/sfatb
```

---

