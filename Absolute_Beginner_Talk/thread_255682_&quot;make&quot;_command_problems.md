---
title: "&quot;make&quot; command problems"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by bollocks00 on 2006-09-11
I'm trying to get wireless set up on my laptop, and I am having some issues. I run dapper drake 6.06 on an IBM z60t (atheros lan chip).  I tried:

cd /usr/src
wget [http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz](http://madwifi.otaku42.de/madwifi-cvs-current.tar.gz)
tar -xzf madwifi-cvs-current.tar.gz
apt-get -y install sharutils
cd /usr/src/madwifi
make clean
make
make install

as per the tutorial at [http://www.ubuntuforums.org/showthread.php?t=75451](http://www.ubuntuforums.org/showthread.php?t=75451) and everything runs smoothly up to the "make clean" command, at which point I get the following:

root@IBM:/usr/src/madwifi-0.9.2# make clean
/bin/sh: line 0: cd: /lib/modules/2.6.15-23-386/build: No such file or directory
Makefile.inc:89: *** /lib/modules/2.6.15-23-386/build is missing, please set KERNELPATH. Stop.

I have tried searching on the forums, but I'm not so great with linux just yet and I can't seem to find what I need. I have already tried updating everything with the newest /etc/apt/sources.list file (last updated today) and I'm still having the same problem. Any thoughts? I would imagine it's something simple that I'm missing.

Thanks.

---

### Post by ewl1217 on 2006-09-11
Have you installed the "build-essential" package? If you haven't, I reccommend that you do. Use the following command:
```
sudo apt-get install build-essential
```

**EDIT:** You may also need to enter the "make" commands with root by using "sudo" before the command. You'll at least need to do that if you want all users on the system to be able to use it.

---

### Post by bollocks00 on 2006-09-11
I had tried that, but no luck.  It turns out

sudo apt-get install build-essential linux-headers-`uname -r`

is what fixed the problem.  Thanks!

---

