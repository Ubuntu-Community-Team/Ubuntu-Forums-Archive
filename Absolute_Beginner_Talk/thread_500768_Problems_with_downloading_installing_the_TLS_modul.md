---
title: "Problems with downloading installing the TLS module for aMsn"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by rover on 2007-07-14
I installed aMsn, tried to login and it asked me to install a TLS protocol for it.
I selected Linux-x86, it downloads and at the end of the download it gives this error: 

> There was an error at the installing of the TLS module:: Couldn't get [http://switch.dl.sourceforge/net/amsn/tls-1.5.0-linux-x86.tar.gz](http://switch.dl.sourceforge/net/amsn/tls-1.5.0-linux-x86.tar.gz)

So I headed to the site and download the package, unzipped it and tried to login again at aMsn, but it still asked me to install the TLS module.

Can anyone help me in this matter?
Do I need to compile-install the unzipped files?

---

### Post by starsky on 2007-07-14
> **rover said:**
> I installed aMsn, tried to login and it asked me to install a TLS protocol for it.
I selected Linux-x86, it downloads and at the end of the download it gives this error: 



So I headed to the site and download the package, unzipped it and tried to login again at aMsn, but it still asked me to install the TLS module.

Can anyone help me in this matter?
Do I need to compile-install the unzipped files?

Hi there :)

Yes, you need to unzip the file and install it.

it's not that hard.

do this inside the directory you unzipped tls 
$ ./configure 
$ make
$ make install

post back :)

HTH

---

### Post by kukibird1 on 2007-07-14
Open a terminal  and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50

Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 

Restart Amsn

---

### Post by starsky on 2007-07-14
> **kukibird1 said:**
> Open a terminal  and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50

Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 

Restart Amsn

oh! so they make binary tls module ? damn. didn't know about that. :)

---

### Post by kukibird1 on 2007-07-14
The Amsn client has trouble trying to download this same file.  I just did it manually and put it in the correct directory. I'm not sure  if it is a binary myself .

---

### Post by Free Penguin on 2007-07-15
look this: [www.freepenguin.it/tip8.html](www.freepenguin.it/tip8.html)

(it's in italian but I think you can easily understand)

Free Penguin

---

### Post by raul_ on 2007-07-15
Why 2 threads about the same thing?

---

### Post by regomodo on 2007-07-25
> **kukibird1 said:**
> Open a terminal  and issue the following commands .

wget [http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz](http://internap.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz) 
tar xvzf tls-1.5.0-linux-x86.tar.gz 
sudo cp -f ~/tls1.50/* /usr/lib/tls1.50

Make sure /usr/lib/tls1.50 is set in the  tools>preferences>advanced options menu in Amsn. 

Restart Amsn

Grr. Unfortunately that doesn't work for me. Why is this problem not fixed yet?

{EDIT} Did another restart of aMSN and now it works. w00t!

---

### Post by OliverN on 2007-09-20
-

---

### Post by TrashmanL on 2007-11-05
I've tried everything above, nothing works for me. I copied the TLS files to /usr/lib/tls1.50 and I entered the path under TLS in the preferences in aMSN, and it still cannot find it, says it appears it is not installed.

---

