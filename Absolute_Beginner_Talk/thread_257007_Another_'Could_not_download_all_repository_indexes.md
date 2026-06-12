---
title: "Another 'Could not download all repository indexes'"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by jpick_21 on 2006-09-13
For the life of me I can't figure out what's wrong.  I have been reading posts and trying different things but I can't seem to get the updates/software installs to work.  The error message I get is

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.7 80]

Of course I can hit the URLs in firefox with no problem.  Below is my sources.list file.  Any help would be greatly appreciated.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by jpick_21 on 2006-09-14
I have returned to the original file with the same error message.

The error

[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) Connection failed [IP: 195.248.90.23 80]



The file

## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
# or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by ComplexNumber on 2006-09-14
if you can browse the web using firefox but you can't download software from the repositories, have a read of this because i was(still am) having the same problem:
[http://www.ubuntuforums.org/showthread.php?t=250832](http://www.ubuntuforums.org/showthread.php?t=250832)

---

### Post by jpick_21 on 2006-09-14
Thanks for the link.  I do have a linksys firewall setup so maybe that's the problem.  I tried to manually ftp a file from the archive.ubuntu.com website and this is what I got.

ftp> get override.warty.restricted
local: override.warty.restricted remote: override.warty.restricted
200 PORT command successful. Consider using PASV.
150 Opening BINARY mode data connection for override.warty.restricted (3513 bytes).
226 File send OK.
3513 bytes received in 0.00 secs (3811.8 kB/s)
ftp>

I then quit the ftp program and did an ls to find

-rw-r--r--  1 jmoore jmoore 3513 2006-09-14 19:34 override.warty.restricted

which makes me think its not a firewall issue as the file looks fine.

---

