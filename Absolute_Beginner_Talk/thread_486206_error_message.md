---
title: "error message"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by halesquad on 2007-06-27
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do i do ?


Thanks

---

### Post by bodhi.zazen on 2007-06-27
Open a terminal and enter :

```
sudo dpkg --configure -a
```

What were your doing/installing ?

---

### Post by halesquad on 2007-06-27
i was playing around with affinity i think and then it uninstalled a great long list of programs and then i got this message after it froze and i quit the terminal.

---

### Post by halesquad on 2007-06-27
stephen@stephen-desktop:~$ sudo dpkg --configure -a
Password:
Setting up bridge-utils (1.2-1build1) ...

Setting up evolution-data-server-common (1.10.1-0ubuntu1.1) ...
Setting up oss-linux (v4.0-1002) ...
Building OSS Modules for Linux-unknown 2.6.20-16-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
Previous start of OSS crashed the system
Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.
dpkg: error processing oss-linux (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up heliodor (0.2.1-0ubuntu1) ...

Setting up libxerces27 (2.7.0-3) ...

Setting up emerald-dbg (0.2.0~0beryl1) ...
Setting up libemeraldengine0-dbg (0.2.0~0beryl1) ...
Setting up kwin (3.5.6-0ubuntu20.1) ...

Setting up arkeia (6.0.8-0ubuntu1) ...
arkeiad is starting ...
arkeiad is already running. Stopping it ...
arkeiad is starting ...
Error: Too much caracters '=' found in the command line
arkc error: Add '-moreinfo' option to get more information
dpkg: error processing arkeia (--configure):
 subprocess post-installation script returned error exit status 21
Setting up libxalan110 (1.10-3) ...

Setting up libtrackerclient0 (0.5.4-4) ...

Setting up heliodor-dbg (0.2.0~0beryl1) ...
Setting up aquamarine (0.2.1.dfsg+git20070318-0ubuntu2) ...

Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up affinity (0.1-1) ...
Setting up aquamarine-dbg (0.2.0~0beryl1) ...
Errors were encountered while processing:
 oss-linux
 arkeia
stephen@stephen-desktop:~$

---

### Post by halesquad on 2007-06-27
E: arkeia: subprocess post-installation script returned error exit status 21
E: oss-linux: subprocess post-installation script returned error exit status 1


more error messages after doing the updates

---

### Post by halesquad on 2007-07-02
i am still getting the error message about oss-linux as above. 

I know that it is to do with the open source sound but don't know how to fix it

---

### Post by bodhi.zazen on 2007-07-02
Well, the output gives a clue perhaps ?

> [b][color=red]Please resolve the situation and remove file
"/usr/lib/oss/starting". Then start OSS by
running soundon again.[/b][/color]
dpkg: error processing oss-linux (--configure):
subprocess post-installation script returned error exit status 1

Try that in a terminal ;)

I also found this :

[http://ubuntuforums.org/showthread.php?p=2822057](http://ubuntuforums.org/showthread.php?p=2822057)

Which was not encouraging :(

You can try ```
sudo apt-get --purge oss-linux
sudo apt-get install oss-linux
```

---

### Post by H0tSh0t on 2007-07-03
I get the same problem I have figured out how to remove /usr/lib/oss/starting
however i dont know how to [COLOR="Red"] start OSS by
running soundon again.[/COLOR]

---

