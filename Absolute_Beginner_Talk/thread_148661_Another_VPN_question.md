---
title: "Another VPN question"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by blx_286 on 2006-03-22
I am having trouble getting my head around this vpn setup. I have tried several things in the various vpn threads, but I am still stuck. The last setup I tried was using the instructions provided by that McMasters University. Everthing looked ok, but when trying to initialize it, I got that Insmod error. So, I thought I would start over and this is where I am at:

root@blackhole:/usr/src# sudo apt-get install build-essential gcc-3.4 linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-image-2.6.12-10-386 is already the newest version.
The following extra packages will be installed:
cpp-3.4 gcc-3.4-base linux-headers-2.6.12-10
Suggested packages:
gcc-3.4-doc libc6-dev-amd64
The following NEW packages will be installed:
cpp-3.4 gcc-3.4 gcc-3.4-base linux-headers-2.6.12-10
linux-headers-2.6.12-10-386
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 9116kB of archives.
After unpacking 79.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gcc-3.4-base 3.4.4-6ubuntu8.1 [163kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main cpp-3.4 3.4.4-6ubuntu8.1 [1707kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gcc-3.4 3.4.4-6ubuntu8.1 [517kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10 2.6.12-10.30 [5927kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10-386 2.6.12-10.30 [802kB]
Fetched 9116kB in 47s (191kB/s)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 72413 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-10.
Unpacking linux-headers-2.6.12-10 (from .../linux-headers-2.6.12-10_2.6.12-10.30_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-10-386.
Unpacking linux-headers-2.6.12-10-386 (from .../linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8.1) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8.1) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8.1) ...
Setting up linux-headers-2.6.12-10 (2.6.12-10.30) ...

Setting up linux-headers-2.6.12-10-386 (2.6.12-10.30) ...
root@blackhole:/usr/src# ls
linux-headers-2.6.12-10 linux-headers-2.6.12-10-386
root@blackhole:/usr/src# rm -r linux-headers-2.6.12-10-386
root@blackhole:/usr/src# ln -s linux linux-source-2.6.12-10
root@blackhole:/usr/src# ln -s linux-headers linux-headers-2.6.12-10

I don't know what I did wrong, but /usr/src showed two different headers, so I deleted one. And the linux-source is showing as a broken link.

Sorry for the long post, but if someone could point me in the right direction I would appreciate it.

Thanks,
Tim

---

### Post by yooper4ever on 2006-03-22
I'm new at this too but I think I got it working. I don't think you should've deleted either headers file. Try re-installing the one that you deleted with the "apt-get" command.

Also, look here:
[http://www.ubuntuforums.org/showthread.php?t=108895&highlight=vpn+cisco+install](http://www.ubuntuforums.org/showthread.php?t=108895&highlight=vpn+cisco+install)

To see if you can get more info....

---

### Post by blx_286 on 2006-03-22
Thanks for the link. That was one of the threads that I looked through.

I was wondering if I only need one of those header files and if so, which one. Also I'm not sure how to fix the other broken sym link. And I guess the last thing is with the gcc file, how do I make sure it points to the one I downloaded. ](*,)

---

### Post by celloandy on 2006-03-22
You don't want to delete either of them, because apt and other programs now think something is there that you've deleted, which could cause problems.  I'd suggest reinstalling the header package to restore what got erased.

Andrew

---

### Post by blx_286 on 2006-03-23
Thanks guys, that worked. I reinstalled that other header, disregarded the broken symbolic link, and ran the vpn install again.

It does connect and I got the profile setup. For some reason, I have to run that /etc/init.d/vpnclient_init start before it will start.

Now I'm back to search the threads to see if I can fix that init thing and see if there is a GUI for the VPN client.

Thanks,
Tim

---

