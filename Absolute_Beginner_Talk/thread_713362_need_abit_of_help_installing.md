---
title: "need abit of help installing"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-03-02
trying to install wesside-ng part of the aircrack package 

got this from another forum on how to install 

Anyway, wesside-ng is part of the standard aircrack 1.0-dev package. All you have to do is download the trunk 1.0-dev (beta 2) package, "make" it, and "make install" and lo and behold, you'll have wesside-ng and all the latest development tools make by the aircrack dev team.

[http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/)

More specifically, regardless which distro of linux you have to install:

Quote:
svn co [http://trac.aircrack-ng.org/svn/trunk/](http://trac.aircrack-ng.org/svn/trunk/)


Quote:
cd trunk


Quote:
make


Quote:
make install


That is all. Of course, this assumes you have svn and all the dependencies installed. If you get a compile error, 99% chance you don't have the dependencies installed. Read the errors and install the dependencies. 



when i do this i get 


Checked out revision 970.
coubury@coubury-desktop:~$ cd trunk
coubury@coubury-desktop:~/trunk$ make
make -C src all
make[1]: Entering directory `/home/coubury/trunk/src'
make -C osdep
make[2]: Entering directory `/home/coubury/trunk/src/osdep'
Building for Linux
make[3]: Entering directory `/home/coubury/trunk/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -fPIC -I.. -c -o osdep.o osdep.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -fPIC -I.. -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -fPIC -I.. -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -fPIC -I.. -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -fPIC -I.. -c -o radiotap-parser.o radiotap-parser.c
ar cru libosdep.a osdep.o network.o linux.o linux_tap.o radiotap-parser.o
ranlib libosdep.a
touch .os.Linux
make[3]: Leaving directory `/home/coubury/trunk/src/osdep'
make[2]: Leaving directory `/home/coubury/trunk/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -Iinclude -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:3981: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:3981: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:3987: warning: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/coubury/trunk/src'
make: *** [all] Error 2
coubury@coubury-desktop:~/trunk$ make install
make -C src install
make[1]: Entering directory `/home/coubury/trunk/src'
make -C osdep
make[2]: Entering directory `/home/coubury/trunk/src/osdep'
Building for Linux
make[3]: Entering directory `/home/coubury/trunk/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/coubury/trunk/src/osdep'
make[2]: Leaving directory `/home/coubury/trunk/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=970 -Iinclude -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:3981: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:3981: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:3987: warning: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/coubury/trunk/src'
make: *** [install] Error 2



when i type wesside-ng in a terminal it says command not found!

---

### Post by Infinite Recursion on 2008-03-22
Unless you are looking for a specific version of wesside-ng, you can try installing the aircrack-ng package using apt-get:
```
sudo apt-get install aircrack-ng
```

This package will install all of the aircrack-ng utilities, including wesside-ng.

Edit: I noticed that the error lines produced by the make command all had "openssl" in them - installing that (if it isn't already) may allow you to build aircrack from source.

---

### Post by nicedude on 2008-05-28
I can confirm I just successfully built the SVN source for aircrack in Ubuntu Hardy 8.04 after having gotten the same errors as reported above. I had already checked all the dependencies were installed and still got the error. So although I already had openssl installed I just checked it for reinstall and also selected libssl development and python & ruby ssl packages just to be sure and bam it worked and make command succeeded with no errors as did the make install. So anyone reading this try doing this and it should work for you as well :-)

---

### Post by jimmyridge on 2008-06-16
sudo aptitude install libssl-dev

---

### Post by Moeng on 2008-07-08
> **jimmyridge said:**
> sudo aptitude install libssl-dev

This fixed it for me

---

