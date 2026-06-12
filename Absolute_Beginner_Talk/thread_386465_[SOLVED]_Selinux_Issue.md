---
title: "[SOLVED] Selinux Issue"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by victorbrca on 2007-03-17
Hi all,

  When I was trying to install Pam_keyring as per this post [_*Link*_]("http://ubuntuforums.org/showthread.php?t=349984"), I got a lot of question in regards to Selinux. The install failed.

  Now I've just tried to install Epiphany and I'm getting more errors... Can anyone help me!!!! :frown: 

```
Setting up selinux-policy-default (1.26-7) ...
cat: /selinux/policyvers: No such file or directory
Compiling policy ...
policyvers value 0 not in range 15-20
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-20)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Setting up hermes1 (1.3.3+really1.3.2-5.1) ...

Setting up libclanlib2c2a (0.6.5-1-3.1ubuntu1) ...

Setting up libclan2c2a-sound (0.6.5-1-3.1ubuntu1) ...

Setting up epiphany-data (0.5.1-4) ...
Setting up epiphany (0.5.1-4) ...

Errors were encountered while processing:
 selinux-policy-default
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up selinux-policy-default (1.26-7) ...
cat: /selinux/policyvers: No such file or directory
Compiling policy ...
policyvers value 0 not in range 15-20
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-20)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 selinux-policy-default

```


Thanks a lot...


Vic.

---

### Post by Najand on 2007-03-17
Try to remove all partial downloads and clean/autoclean your apt using these commands:
```

$sudo rm /var/lib/apt/lists/partial/*
$sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update

```
And try again.

---

### Post by victorbrca on 2007-03-17
Hi Najand,


  Thanks for the reply.

  I tried it and go the same error when installing Epiphany. There was no file on "/var/lib/apt/lists/partial/*".
  Apt clean, autoclean and update did not retun any errors...


Vic.

---

### Post by victorbrca on 2007-03-18
Does anyone knows if uninstalling selinux would resolve this issue ??

Thanks,

Vic.

---

### Post by victorbrca on 2007-04-02
**SOLVED**

[**_Source_**]("http://ubuntuforums.org/showthread.php?t=343280")

> Run

dpkg --purge selinux-policy-default

to get rid of the broken selinux-policy-default package.

Maybe request the removal of the package from Ubuntu, and try to get some people together to start working on a decent SELinux support in Ubuntu. AFAICT it's pretty much nonexistent.

---

