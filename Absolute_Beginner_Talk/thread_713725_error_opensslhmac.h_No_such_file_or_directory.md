---
title: "error: openssl/hmac.h: No such file or directory"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by coubury on 2008-03-03
trying to install 1.0 beta2

coubury@coubury-desktop:~$ wget [http://download.aircrack-ng.org/aircrack-ng-1.0-beta2.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.0-beta2.tar.gz)
--07:06:37--  [http://download.aircrack-ng.org/aircrack-ng-1.0-beta2.tar.gz](http://download.aircrack-ng.org/aircrack-ng-1.0-beta2.tar.gz)
           => `aircrack-ng-1.0-beta2.tar.gz.3'
Resolving download.aircrack-ng.org... 213.186.33.2
Connecting to download.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 967,590 (945K) [application/x-tar]

100%[====================================>] 967,590       52.17K/s    ETA 00:00

07:06:54 (57.48 KB/s) - `aircrack-ng-1.0-beta2.tar.gz.3' saved [967590/967590]

coubury@coubury-desktop:~$ cd aircrack-ng-1.0-beta2
coubury@coubury-desktop:~/aircrack-ng-1.0-beta2$ make install
make -C src install
make[1]: Entering directory `/home/coubury/aircrack-ng-1.0-beta2/src'
make -C osdep
make[2]: Entering directory `/home/coubury/aircrack-ng-1.0-beta2/src/osdep'
Building for Linux
make[3]: Entering directory `/home/coubury/aircrack-ng-1.0-beta2/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/coubury/aircrack-ng-1.0-beta2/src/osdep'
make[2]: Leaving directory `/home/coubury/aircrack-ng-1.0-beta2/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=`../evalrev`  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:63:
[B][U]crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory[/U][/B]
cc1: warnings being treated as errors
aircrack-ng.c: In function ‘do_wpa_crack’:
aircrack-ng.c:3981: warning: implicit declaration of function ‘HMAC’
aircrack-ng.c:3981: warning: implicit declaration of function ‘EVP_sha1’
aircrack-ng.c:3987: warning: implicit declaration of function ‘EVP_md5’
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/coubury/aircrack-ng-1.0-beta2/src'
make: *** [install] Error 2
coubury@coubury-desktop:~/aircrack-ng-1.0-beta2$



now i see the error (in bold i checked on the aircrack wiki page and it said about downloading openSLL i went to synaptic and downloaded it yet im still getting the same erorr message

---

### Post by lloyd_b on 2008-03-03
You don't specify which package you installed for OpenSSL, so this may or may not be relevant...

Try installing the package "libssl-dev".  This contains the development headers, which is what it appears you are missing.

Lloyd B.

---

### Post by Anicka on 2008-03-03
Is there any specific reason why you're not installing the aircrack-ng from the repos? All dependencies would be automatically resolved.```
sudo aptitude install aircrack-ng
```

---

### Post by brew1988 on 2008-04-16
> **lloyd_b said:**
> You don't specify which package you installed for OpenSSL, so this may or may not be relevant...

Try installing the package "libssl-dev".  This contains the development headers, which is what it appears you are missing.

Lloyd B.

i have the same problem
i've installed openssl-0.9.8g, is the libssl-dev package included, or do i need to do some futher installations. 
if so how as i've just recently come over from the dark side (windows) and i'm have a little trouble working out the in and outs of ubuntu

cheers

---

### Post by lloyd_b on 2008-04-16
> **brew1988 said:**
> i have the same problem
i've installed openssl-0.9.8g, is the libssl-dev package included, or do i need to do some futher installations. 
if so how as i've just recently come over from the dark side (windows) and i'm have a little trouble working out the in and outs of ubuntu

cheers

The package "libssl.0.9.8" (which is what I'm assuming you installed) contains the actual libraries, but *not* the development headers.  You'll still need to install the package "libssl-dev" to get those headers.

Note that this is extremely common with Linux in general and Debian based distros (such as Ubuntu) in particular.  The base libraries, which are needed to *run* programs using the library, are in one package, while the development headers, which are needed to *compile* programs against the library, are in another.

Note: to install the package, either "sudo apt-get install libssl-dev" in a terminal window, or use a GUI based package manager such as Synaptic (it should be in your "System" menu).

Lloyd B.

---

### Post by openflame06 on 2008-04-26
Just a note - when building any program if you get an error about a certain thing think of the package it will be in.

If you look on the aircrack-ng site it actually states the packages you will need including libssl-dev and I think also libpcap and a few others.

---

