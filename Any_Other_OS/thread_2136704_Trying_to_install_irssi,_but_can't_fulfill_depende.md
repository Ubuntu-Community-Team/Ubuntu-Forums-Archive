---
title: "Trying to install irssi, but can't fulfill dependencies; broken packages"
date: 2013-04-18
forum: Any Other OS
---

### Post by anthony62490 on 2013-04-18
I installed Debian 6.0.7 a few days ago, and I have been able to find the answers to most of my questions through heavy application of google, but this one has me stumped. I am trying to install the IRC client Irssi, but I can't seem to meet the dependencies. Here's what I get.

```
anthony@debian-vb:~$ sudo apt-get install irssi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 irssi : Depends: libperl5.10 (>= 5.10.1) but it is not going to be installed
E: Broken packages

```

So it depends on libperl5.10? Okay then, I'll install that as well.
```
anthony@debian-vb:~$ sudo apt-get install libperl5.10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libperl5.10 : Depends: perl-base (= 5.10.1-17squeeze5) but 5.10.1-17squeeze6 is to be installed
E: Broken packages

```

So this package depends on perl-base? I'll try to install that, then.
```
anthony@debian-vb:~$ sudo apt-get install perl-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
perl-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

**So now I don't know what to do. It looks like at least 2 packages are in an unusable state.**
Misc. Troubleshooting attempts:
```
anthony@debian-vb:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

anthony@debian-vb:~$ sudo dpkg --configure -a
anthony@debian-vb:~$ 

```

/ect/apt/sources.list
```
# 
deb http://ftp.us.debian.org/debian stable main contrib non-free
deb-src http://ftp.debian.org/debian/ squeeze-updates main contrib non-free
deb-src http://security.debian.org/ squeeze/updates main contrib non-free

#Third Party repos
#Debian Multimedia
deb http://www.las.ic.unicamp.br/pub/debian-multimedia/ stable main
#Debian Mozilla Team
deb http://backports.debian.org/debian-backports squeeze-backports main

```

So what do you think? Am I missing something? Why are my packages broken? It looks like my PC already has some form of Perl library installed. Are the two conflicting?

---

### Post by oldos2er on 2013-04-18
Moved to Other OS/Distro Support.

---

