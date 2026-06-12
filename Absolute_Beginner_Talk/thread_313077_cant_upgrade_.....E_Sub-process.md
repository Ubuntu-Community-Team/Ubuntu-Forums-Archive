---
title: "cant upgrade .....E: Sub-process"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by msn4us on 2006-12-05
hi guyz..

from yesterday i can make upgrade 

```
root@ndc-laptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  bash bsdutils debianutils diff dpkg e2fslibs e2fsprogs findutils grep gzip
  hostname libblkid1 libcomerr2 libdevmapper1.02 libncurses5 libslang2 libss2
  libuuid1 login lsb-base mount ncurses-base ncurses-bin perl-base
  python-minimal python2.4-minimal sed sysv-rc sysvutils tar util-linux zlib1g
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8189kB of archives.
After unpacking 29.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@ndc-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ndc-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ndc-laptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  bash bsdutils debianutils diff dpkg e2fslibs e2fsprogs findutils grep gzip
  hostname libblkid1 libcomerr2 libdevmapper1.02 libncurses5 libslang2 libss2
  libuuid1 login lsb-base mount ncurses-base ncurses-bin perl-base
  python-minimal python2.4-minimal sed sysv-rc sysvutils tar util-linux zlib1g
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8189kB of archives.
After unpacking 29.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  debianutils libncurses5 bash bsdutils diff dpkg e2fslibs libdevmapper1.02
  libblkid1 libcomerr2 libss2 libuuid1 e2fsprogs findutils grep gzip hostname
  login mount ncurses-bin perl-base sed sysv-rc sysvutils tar lsb-base
  libslang2 zlib1g util-linux ncurses-base python2.4-minimal python-minimal
Install these packages without verification [y/N]? y
E: Cannot get debconf version. Is debconf installed?
Extracting templates from packages: 93%E: Cannot get debconf version. Is debconf installed?
Extracting templates from packages: 100%d file descriptor
(Reading database ... 3323 files and directories currently installed.)
Unpacking debianutils (from .../debianutils_2.17.3_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
\nPlease upgrade to a newer version of dpkg\n
dpkg: error processing /var/cache/apt/archives/debianutils_2.17.3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/debianutils_2.17.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ndc-laptop:~# 


```


i will i do now ...can any body help me](*,) ](*,) ](*,)

---

### Post by msn4us on 2006-12-05
nobody waanna help](*,)

---

### Post by rbprogrammer on 2006-12-05
up at the top of your text from the konsole it says
> root@ndc-laptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  bash bsdutils debianutils diff dpkg e2fslibs e2fsprogs findutils grep gzip
  hostname libblkid1 libcomerr2 libdevmapper1.02 libncurses5 libslang2 libss2
  libuuid1 login lsb-base mount ncurses-base ncurses-bin perl-base
  python-minimal python2.4-minimal sed sysv-rc sysvutils tar util-linux zlib1g
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8189kB of archives.
After unpacking 29.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

just out of curiosity, why did you choose no?  i though you wanted a distribution upgrade....

---

### Post by msn4us on 2006-12-05
> just out of curiosity, why did you choose no? i though you wanted a distribution upgrade....
Reply With Quote


first time i select no ..but 2nd time i select yes u can see it 

but still now i dont know what should i do](*,) ](*,)

---

### Post by d3v1ant_0n3 on 2006-12-05
Again, just out of interest, why are you running as root?

*edit*  I had a better read of your output-it shows debconf as not installed...what happens if you do:

```
sudo aptitude install debconf
```

Although if it doesn't have dpkg and/or debconf (as it looks like from that output) I'm not sure how it'll install new packages at all. Um. I might be stumped on this one.

---

### Post by msn4us on 2006-12-05
> Again, just out of interest, why are you running as root?


coz the x server not work

so i work in the command line

so still now i cant install and remove anything

also cant upgrade](*,) ](*,)

---

### Post by d3v1ant_0n3 on 2006-12-05
```
sudo dpkg-reconfigure xorg-xserver
```

Should bring up a dialog to help you reconfigure X.

Did the command I put up in my last post help any?

---

### Post by sourchier on 2006-12-05
What happens when you try sudo aptitude autoclean, and then sudo aptitude update, any error messages? Could you post your sources.conf?

---

### Post by msn4us on 2006-12-05
```
root@ndc-laptop:~# sudo aptitude install debconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  gnupg libgnutls13 libopencdk8 libssl0.9.8 
The following packages have been kept back:
  debconf-i18n gcc-4.1-base libgcc1 libldap2 libreadline5 libsasl2 
  libsasl2-modules libstdc++6 libtasn1-3 makedev perl-base readline-common 
0 packages upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libopencdk8: Depends: zlib1g (>= 1:1.2.1) but it is not installable
  libgnutls13: Depends: zlib1g (>= 1:1.2.1) but it is not installable
  libssl0.9.8: Depends: zlib1g (>= 1:1.2.1) but it is not installable
  gnupg: Depends: zlib1g (>= 1:1.2.1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
zlib1g [1:1.2.3-13ubuntu3 (feisty)]

Score is -16

Accept this solution? [Y/n/q/?] Y
The following NEW packages will be automatically installed:
  zlib1g 
The following packages have been kept back:
  debconf-i18n gcc-4.1-base gnupg libgcc1 libgnutls13 libldap2 libopencdk8 
  libreadline5 libsasl2 libsasl2-modules libssl0.9.8 libstdc++6 libtasn1-3 
  makedev perl-base readline-common 
The following NEW packages will be installed:
  zlib1g 
0 packages upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/71.7kB of archives. After unpacking 164kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 4334 files and directories currently installed.)
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3-13ubuntu3_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !

You must upgrade dpkg before installing this package.

dpkg: error processing /var/cache/apt/archives/zlib1g_1%3a1.2.3-13ubuntu3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/zlib1g_1%3a1.2.3-13ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libssl0.9.8:
 libssl0.9.8 depends on zlib1g (>= 1:1.2.1); however:
  Package zlib1g is not installed.
dpkg: error processing libssl0.9.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnupg:
 gnupg depends on zlib1g (>= 1:1.2.1); however:
  Package zlib1g is not installed.
dpkg: error processing gnupg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2-modules:
 libsasl2-modules depends on libssl0.9.8 (>= 0.9.8b-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libsasl2-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-keyring:
 ubuntu-keyring depends on gnupg (>= 1.0.6-4); however:
  Package gnupg is not configured yet.
dpkg: error processing ubuntu-keyring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libopencdk8:
 libopencdk8 depends on zlib1g (>= 1:1.2.1); however:
  Package zlib1g is not installed.
dpkg: error processing libopencdk8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2:
 libsasl2 depends on libsasl2-modules (= 2.1.19.dfsg1-0.2ubuntu3) | libsasl2-modules-sql (= 2.1.19.dfsg1-0.2ubuntu3) | libsasl2-modules-gssapi-heimdal (= 2.1.19.dfsg1-0.2ubuntu3) | libsasl2-modules-kerberos-heimdal (= 2.1.19.dfsg1-0.2ubuntu3); however:
  Package libsasl2-modules is not configured yet.
  Package libsasl2-modules-sql is not installed.
  Package libsasl2-modules-gssapi-heimdal is not installed.
  Package libsasl2-modules-kerberos-heimdal is not installed.
dpkg: error processing libsasl2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnutls13:
 libgnutls13 depends on libopencdk8 (>= 0.5.8); however:
  Package libopencdk8 is not configured yet.
 libgnutls13 depends on zlib1g (>= 1:1.2.1); however:
  Package zlib1g is not installed.
dpkg: error processing libgnutls13 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libldap2:
 libldap2 depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not configured yet.
 libldap2 depends on libsasl2 (>= 2.1.19.dfsg1); however:
  Package libsasl2 is not configured yet.
dpkg: error processing libldap2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libssl0.9.8
 gnupg
 libsasl2-modules
 ubuntu-keyring
 libopencdk8
 libsasl2
 libgnutls13
 libldap2
root@ndc-laptop:~# 

```

---

### Post by scc4fun on 2006-12-05
> **msn4us said:**
> hi guyz..

from yesterday i can make upgrade 

```
<snip aborted code />
root@ndc-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
<snip second apt-get upgrade />
root@ndc-laptop:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  bash bsdutils debianutils diff dpkg e2fslibs e2fsprogs findutils grep gzip
  hostname libblkid1 libcomerr2 libdevmapper1.02 libncurses5 libslang2 libss2
  libuuid1 login lsb-base mount ncurses-base ncurses-bin perl-base
  python-minimal python2.4-minimal sed sysv-rc sysvutils tar util-linux zlib1g
0 upgraded, 32 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8189kB of archives.
After unpacking 29.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  debianutils libncurses5 bash bsdutils diff dpkg e2fslibs libdevmapper1.02
  libblkid1 libcomerr2 libss2 libuuid1 e2fsprogs findutils grep gzip hostname
  login mount ncurses-bin perl-base sed sysv-rc sysvutils tar lsb-base
  libslang2 zlib1g util-linux ncurses-base python2.4-minimal python-minimal
Install these packages without verification [y/N]? y
E: Cannot get debconf version. Is debconf installed?
Extracting templates from packages: 93%E: Cannot get debconf version. Is debconf installed?
Extracting templates from packages: 100%d file descriptor
(Reading database ... 3323 files and directories currently installed.)
Unpacking debianutils (from .../debianutils_2.17.3_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !
\nPlease upgrade to a newer version of dpkg\n
dpkg: error processing /var/cache/apt/archives/debianutils_2.17.3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/debianutils_2.17.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ndc-laptop:~# 


```


i will i do now ...can any body help me](*,) ](*,) ](*,)

> **rbprogrammer said:**
> up at the top of your text from the konsole it says


just out of curiosity, why did you choose no?  i though you wanted a distribution upgrade....

Keep reading in the code. He has a problem with "debconf".

---

### Post by msn4us on 2006-12-05
so when i make upgrade its give me

```
root@ndc-laptop:~# apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  bash bsdutils debianutils diff dpkg e2fslibs e2fsprogs findutils gpgv grep
  gzip hostname libblkid1 libcomerr2 libdevmapper1.02 libsasl2-2 libslang2
  libss2 libuuid1 login lsb-base mount ncurses-base ncurses-bin python-minimal
  python2.4-minimal sed sysvutils tar util-linux zlib1g
The following packages will be upgraded:
  debconf-i18n gcc-4.1-base gnupg libgcc1 libgnutls13 libldap2 libopencdk8
  libreadline5 libsasl2 libsasl2-modules libssl0.9.8 libstdc++6 libtasn1-3
  makedev perl-base readline-common
16 upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B/13.4MB of archives.
After unpacking 26.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 4334 files and directories currently installed.)
Unpacking zlib1g (from .../zlib1g_1%3a1.2.3-13ubuntu3_i386.deb) ...
dpkg not recorded as installed, cannot check for epoch support !

You must upgrade dpkg before installing this package.

dpkg: error processing /var/cache/apt/archives/zlib1g_1%3a1.2.3-13ubuntu3_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/zlib1g_1%3a1.2.3-13ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ndc-laptop:~# 


```


](*,) ](*,) ](*,)

---

### Post by tbroderick on 2006-12-05
Are you using Edgy and want to dist-upgrade to Feisty? Or are you trying to go from Hoary to Feisty?

---

### Post by msn4us on 2006-12-05
any one can help:confused: :confused:

---

### Post by d3v1ant_0n3 on 2006-12-05
```
 sudo aptitude install dpkg
``` ? Just a guess.It looks like dpkg is either outdated or not present for some reason (as I understand it, dpkg is essential to debian based distros?). I'm not sure how installing dpkg works when dpkg isn't installed or working tho- surely you need dpkg to install programs, and so to install dpkg to a working state, you need dpkg in a working state.

*head explodes*

---

### Post by tbroderick on 2006-12-05
> **msn4us said:**
> any one can help:confused: :confused:

I'll ask again. What version of Ubuntu are you currently using? Cause the thread tags says hoary and you appear to be upgrading to feisty. I don't know if going from hoary to feisty is a good thing. You are skipping two other releases (dapper and edgy).

---

### Post by msn4us on 2006-12-05
```

Code:

sudo aptitude install dpkg

? Just a guess.It looks like dpkg is either outdated or not present for some reason (as I understand it, dpkg is essential to debian based distros?). I'm not sure how installing dpkg works when dpkg isn't installed or working tho- surely you need dpkg to install programs, and so to install dpkg to a working state, you need dpkg in a working state.

*head explodes*
```


thanks my friend now its work with me:mrgreen: 




i never forget ur help:D :D

---

### Post by d3v1ant_0n3 on 2006-12-05
Well yay that it worked. It really was an absolute guess. If something won't work in terminal, it's worth examining the output and trying to troubleshoot the error message it gives you- I figured this out trying to learn to compile programs.

I still don't understand how dpkg can install when dpkg is broken tho- surely dpkg is NEEDED to install anything? can someone enlighten me to this?

---

### Post by scc4fun on 2006-12-06
> **d3v1ant_0n3 said:**
> Well yay that it worked. It really was an absolute guess. If something won't work in terminal, it's worth examining the output and trying to troubleshoot the error message it gives you- I figured this out trying to learn to compile programs.

I still don't understand how dpkg can install when dpkg is broken tho- surely dpkg is NEEDED to install anything? can someone enlighten me to this?
I think it was installed, but for feisty it wanted the new(est?) version of dpkg installed.

---

