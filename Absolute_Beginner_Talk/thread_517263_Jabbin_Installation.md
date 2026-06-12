---
title: "Jabbin Installation"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by anandham on 2007-08-04
Hi,
   I installed Jabbin Latest beta on my Feisty Amd 64 machine using force architecture as Jabbin is only available for i386 architecture. But I'm getting an error message when I'm trying to run the application. 

jabbin: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

libXss is successfully installed. But still I'm getting this error. Please help me.

Thanks
anandham

---

### Post by apswartz on 2007-08-04
Your best bet would be to download the tarball and compile it yourself.

Remove your existing package first.

Then, download the package...
[http://downloads.sourceforge.net/jabbin/jabbin-2.0beta2a.tar.bz2?modtime=1156537602&big_mirror=0](http://downloads.sourceforge.net/jabbin/jabbin-2.0beta2a.tar.bz2?modtime=1156537602&big_mirror=0)

go to the directory where you downloaded it and...
Try first...
```

sudo checkinstall jabbin-2.0beta2a.tar.bz2

```
This option will create a debian package and install that on your system.

If that doesn't work, try this...
```

tar xjf jabbin-2.0beta2a.tar.bz2
cd  jabbin-2.0beta2a
./configure
make
sudo make install

```

---

