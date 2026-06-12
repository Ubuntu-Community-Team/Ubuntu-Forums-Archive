---
title: "error in downloading jde package"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by RAJESHKSV on 2008-03-09
I want to to do programmng  in java in ubuntu gutsy gibbon 7.10.....so I tried to install jde and jdelay and libjdepend-java and some other packages through synaptic package manager...but it showing the following error....Can I negelect it and proceed ??(I have tried more than twice...).plz help:(




E: jde: subprocess post-installation script returned error exit status 1


processing trigeers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 jde
E:Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install .Trying to recover:
Setting up jde(2.3.5.1-2)...
Error in '/usr/share/doc-base/jde',line1:the first line doesnot contain valid
 'Document' field
dpkg:error processing jde( --configure):
 subprocess post-installation script returned error exit status 1
Error were encountered while processing:
jde

---

### Post by jan quark on 2008-03-09
try 

```
sudo dpkg --configure -a
sudo apt-get install -f
```

any error messages?

---

### Post by Angus77 on 2008-04-02
I have the exact same problem, and when I run

```
sudo dpkg --configure -a
sudo apt-get install -f
```

I get

```
$ sudo dpkg --configure -a
Setting up jde (2.3.5.1-2) ...
Error in `/usr/share/doc-base/jde', line 1: the first line does not contain valid `Document' field
dpkg: error processing jde (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 jde

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up jde (2.3.5.1-2) ...
Error in `/usr/share/doc-base/jde', line 1: the first line does not contain valid `Document' field
dpkg: error processing jde (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 jde
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Crypto77 on 2008-04-09
I get the same error as above - any advice?

---

### Post by Angus77 on 2008-04-16
I've got the same problem, too!

---

### Post by _mj on 2008-04-22
Im seeing the same thing.

this should be fixed in the next version of jde which is the default version in ubuntu-Hardy  (out in a few days !!)

see the bug report :
[https://bugs.launchpad.net/ubuntu/+source/jde/+bug/201488](https://bugs.launchpad.net/ubuntu/+source/jde/+bug/201488)

(the url above is messed up) : bugs.launchpad.net/ubuntu/+source/jde/+bug/201488

---

