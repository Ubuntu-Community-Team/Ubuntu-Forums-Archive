---
title: "samba install problem"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by uzi09 on 2006-06-29
hey all, 
i installed samba using the guide on [www.ubuntuguide.org](www.ubuntuguide.org) and ended up getting some error. i continued on ignoring it since i had no idea what it meant, but realized that it would not start no matter what. so i removed it completely and tried reinstalling, i'm getting this error. anyone know what the problem is on this??

```

uzi@mybochs:~$ sudo aptitude install samba
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl
  libnet-ldap-perl libunicode-map-perl libunicode-map8-perl
  libunicode-maputf8-perl smbldap-tools
The following NEW packages will be installed:
  libconvert-asn1-perl libcrypt-smbhash-perl libdigest-md4-perl
  libnet-ldap-perl libunicode-map-perl libunicode-map8-perl
  libunicode-maputf8-perl samba smbldap-tools
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4138kB of archives. After unpacking 11.4MB will be used.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libconvert-asn1-perl.
(Reading database ... 133892 files and directories currently installed.)
Unpacking libconvert-asn1-perl (from .../libconvert-asn1-perl_0.19-1_all.deb) .. .
Selecting previously deselected package libdigest-md4-perl.
Unpacking libdigest-md4-perl (from .../libdigest-md4-perl_1.5-1_i386.deb) ...
Selecting previously deselected package libnet-ldap-perl.
Unpacking libnet-ldap-perl (from .../libnet-ldap-perl_1%3a0.33-2_all.deb) ...
Selecting previously deselected package libunicode-map-perl.
Unpacking libunicode-map-perl (from .../libunicode-map-perl_0.112-9_i386.deb) .. .
Selecting previously deselected package libunicode-map8-perl.
Unpacking libunicode-map8-perl (from .../libunicode-map8-perl_0.12-2_i386.deb) . ..
Selecting previously deselected package libunicode-maputf8-perl.
Unpacking libunicode-maputf8-perl (from .../libunicode-maputf8-perl_1.09-6_all.d eb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_3.0.22-1ubuntu3_i386.deb) ...
Selecting previously deselected package libcrypt-smbhash-perl.
Unpacking libcrypt-smbhash-perl (from .../libcrypt-smbhash-perl_0.12-1_all.deb) ...
Selecting previously deselected package smbldap-tools.
Unpacking smbldap-tools (from .../smbldap-tools_0.9.2-3_all.deb) ...
Setting up libconvert-asn1-perl (0.19-1) ...
Setting up libdigest-md4-perl (1.5-1) ...
Setting up libnet-ldap-perl (0.33-2) ...
Setting up libunicode-map-perl (0.112-9) ...
Setting up libunicode-map8-perl (0.12-2) ...
Setting up libunicode-maputf8-perl (1.09-6) ...
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libcrypt-smbhash-perl (0.12-1) ...
Setting up smbldap-tools (0.9.2-3) ...

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.22-1ubuntu3) ...
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /e tc/init.d/samba
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
uzi@mybochs:~$

```

i think it might be a problem with the source, so in case anyone needs, here's my sources list:
```

uzi@mybochs:~$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

## Ubuntu CD repository
#deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Alpha i386 (20060329.1)]/ dapper main restricted

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free

deb ftp://ftp.nerim.net/debian-marillat/ etch main
deb ftp://ftp.nerim.net/debian-marillat/ experimental main

deb http://xgl.compiz.info/ dapper aiglx
deb http://xgl.compiz.info/ dapper main

#to get the keys for xgl/compiz
deb http://www.beerorkid.com/compiz dapper main

#wine
#deb http://wine.sourceforge.net/apt/ binary/

# new wine
deb http://wine.budgetdedicated.com/apt dapper main
uzi@mybochs:~$

```

please help :(



EDIT:
s0, following up on my assumption of the source having problems, i went ahead and made a backup of my source list and used the original to install samba. it seems to work okay, didn't get any errors, but i haven't yet tried to access it from another machine.

one thing though, what if in our source list we have two different sources for the same program. which one is used first??
for example, if i were downloading samba, and two of my sources provide samba, which one does aptitude go to to download?

---

### Post by woedend on 2006-06-29
the newest one.  IN synaptic, if there are multiple versions of the file, click package menu, then theres an option I think it says Force Version, and choose the ubuntu one.

---

