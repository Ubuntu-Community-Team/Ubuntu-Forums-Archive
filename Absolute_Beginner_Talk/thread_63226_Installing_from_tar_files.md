---
title: "Installing from tar files"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by menawollas on 2005-09-07
There is a file splitter / joiner I find quite useful in windows called HJsplit, and it also comes as a Linux version, so I tried to intall it.

It requires the Kylix library, which I downloaded, untarred, and followed the readme instructions. Seemed OK, doing the followiing in the install.sh
```
#! /bin/sh

install -d /usr/lib/kylix3/
install -m 755 libborqt-6.9.0-qt2.3.so /usr/lib/kylix3/libborqt-6.9.0-qt2.3.so

cd /usr/lib/kylix3/
cp -s libborqt-6.9.0-qt2.3.so libborqt-6.9-qt2.3.so

grep -q "^/usr/lib/kylix3\$" /etc/ld.so.conf
if [ $? == 1 ]; then
  echo /usr/lib/kylix3 >> /etc/ld.so.conf
fi

/sbin/ldconfig
``` 

Then I untarred tarred the app, but when I try to run it it just fails 

(error is 

```
./HJSplitLX: relocation error: ./HJSplitLX: undefined symbol: initPAnsiStrings
```   

Am I missing something obvious? Is it me, hjsplit, ubuntu, or what ?????


Additionaly, if I try and download the command line version, there is a Makefile which you have to make, but when I try this, I get 

```
dave@Muffin:~/Tarz/lxsplit-0.1.1$ make
gcc -c -W -O2 -DNO_DEBUG  -o func.o func.c
make: gcc: Command not found
make: *** [func.o] Error 127
dave@Muffin:~/Tarz/lxsplit-0.1.1$
``` 


I am totally confused, and any help would be welcome.

---

### Post by invalid on 2005-09-07
Well I can't answer all of your post, but I can answer the second half:

The reason it will not make, seems to be from a missing compiler.
Type "sudo apt-get install build-essential" to fix this.

Cheers,
Cb

---

### Post by menawollas on 2005-09-07
Thanks,

got the commadn line bit working  \\:D/

---

