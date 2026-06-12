---
title: "Help with aMSN"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by BrandonB on 2007-08-03
I am pretty sure i have aMSN fully installed I go to applications>>Internet>>aMSN and it comes up and tells me to put in a account and password so I do but when I do it tells me it needs TLS for it then tells me to choose a system type so they can automatically download the files Im not sure which one I should choose there are a few 

Linux-x86
Linux-x86_64
Linux-powerpc
linux-sparc
Netbsd-x86
netbsd-sparc64
freebsd-x86
solaris 2.6 sparc
solaris 2.8 sparc
mac os X
Windows
Source Code (Needs compiling and installing)
Dont download TLS I'll download it myself

I have tried choosing anyone of them but when I choose one of them it says 
aMSN error error installing TLS Module:: couldnt get [http://switch.dl.sourceforge.net/sourceforge/amsn/tls1.5.0-src.tar.gz](http://switch.dl.sourceforge.net/sourceforge/amsn/tls1.5.0-src.tar.gz) 

If anyone could help me I would be so grateful I am very tired of having to use Gaim it is.. well some people might like it but it sure isnt for me

Brandon

---

### Post by kknd on 2007-08-03
Pick the first one, unless you have Ubuntu 64 bits, (then pick the second)

---

### Post by Diabolis on 2007-08-03
do the following:

```
wget http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz

tar xvzf tls-1.5.0-linux-x86.tar.gz

sudo cp -f ~/tls1.50/* /usr/lib/tls1.50/
```

I got it from here: [http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html]("http://www.getautomatix.com/forum/lofiversion/index.php/t1182.html")

Or you can install automatix and get it from there.

---

### Post by profediego on 2007-08-06
Thanks that solved my problem too, :guitar:

---

