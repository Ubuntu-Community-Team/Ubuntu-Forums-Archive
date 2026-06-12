---
title: "Flashplugin-nonfree Archives?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by dothedorky on 2006-11-22
I keep getting this annoying message:

[B]The following problems were found on your system:

E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
[/B]

That, and also when i open up synaptic the whole manager is empty, even when i click 'sections' 'status' 'search' or 'custom' buttons. 

Any ideas?

---

### Post by dothedorky on 2006-11-22
Thought I'd also add this is (what i got when i tried:

[B]wget [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb)
[/B]
and then

[B]sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
[/B]

```
dothedorky@ubuntu:wget http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
--00:48:09--  http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
           => `flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb'
Resolving 3v1n0.tuxfamily.org... 212.85.158.4
Connecting to 3v1n0.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,538,038 (2.4M) [application/x-debian-package]

100%[====================================>] 2,538,038    159.49K/s    ETA 00:00

00:48:27 (138.92 KB/s) - `flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb' saved [2538038/2538038]

dothedorky@ubuntu:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb
Selecting previously deselected package flashplugin-nonfree.
(Reading database ...
dpkg: serious warning: files list file for package `flashplugin-nonfree' missing, assuming package has no files currently installed.
82672 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.21.55-3v1ubuntu0 (using flashplugin-nonfree_9.0.21.78-3v1ubuntu0_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 flashplugin-nonfree depends on libfreetype6 (>= 2.2); however:
  Version of libfreetype6 on system is 2.1.10-1ubuntu2.2.
 flashplugin-nonfree depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 flashplugin-nonfree depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.
dpkg: error processing flashplugin-nonfree (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 flashplugin-nonfree
```

---

### Post by dothedorky on 2006-11-27
Just a bump in case this was unnoticed...

---

