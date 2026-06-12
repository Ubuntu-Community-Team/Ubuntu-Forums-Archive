---
title: "Accessing NFS shares from Mac OSX: Not working ?"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2006-03-27
How to mount a linux share nfs (mount -t nfs)?
==========

Hi !

I would like to mount a linux server. I tried in the MAC to access to my Linux server:
mount -t nfs IPadress:/export /mydestonmymacfolder
And, this is not working.
   
--------
When I use the terminal sh, then, I enter:
mount -t nfs IPaddress:/mnt/exports /mnt/exportsonmac

I get this error msg : mount_nfs: /mnt/home: Operation not permitted

There is something wrong somewhere, i dont know.

Additionally, the linux server is working very well, and all the linux boxes can ping and make use of this exports on the linux server (all ip are correct and working, and sharing either).

Thank you very mmuch if you would find the reason and solution :-)

Patrick

---

