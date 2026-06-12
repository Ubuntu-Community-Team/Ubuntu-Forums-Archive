---
title: "Server and scponly"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by tjm on 2006-06-06
Hi

I can install scponly via apt-get but cannot get it to work. 

I then tried to install it from the source but the setup-script fails:

> i cant find your equivalent of ld.so
make: *** [jail] Error 1

> /lib/ld.so.1 exists but I cannot parse it to ./configure.

(Btw. it's astonishing that the recent release of scponly is 4.6 on the maintainers website but on Ubuntu via apt it is 4.6.1???)

Any ideas how fix this?

---

### Post by tjm on 2006-06-10
I reinstalled scponly using the latest source. After running as root:

> # ln -s /lib/ld.so.1.conf /lib/ld.so.conf
# touch /etc/lib.so.conf

and

> # make jail

the install script worked well, set up the user and its home directory and a writable subdirectory but...

...logging in via SFTP still fails...

> MacMini:~ tjm$ sftp scponly@powerbook           
Connecting to powerbook...
scponly@powerbook's password: 
Connection closed
MacMini:~ tjm$ 

Ubuntulinux Server 6.06 Dapper Drake PowerPC

Any help is very much appreciated!
Tom

---

