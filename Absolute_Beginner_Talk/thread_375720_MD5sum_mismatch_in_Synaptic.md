---
title: "MD5sum mismatch in Synaptic"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Chamith on 2007-03-04
Hi,

I have been getting the following errors from synaptics after a fresh install of Dapper 6.06.  I've tried some of the forums but I haven't been able to solve the errors - any ideas?

Thanks,
Chamith

*****
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) MD5Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

*****
OUTPUT: cat /etc/apt/sources.list

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) dapper-seveas all

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial main

---

### Post by taurus on 2007-03-04
Try something like

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Chamith on 2007-03-04
hey,

thanks for the reply - I received the following errors

*****
OUTPUT Errors: sudo aptitude update
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Sub-process gzip returned an error code (1)

*****
OUTPUT Errors: sudo aptitude upgrade

Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~dapper1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

---

### Post by Chamith on 2007-03-04
oh,

And I get the following errors in Synaptics

*****
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) MD5Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

---

### Post by Chamith on 2007-03-05
Hey - now I'm getting an extra error - although I haven't done anything to my sources!!

Does anyone know what these errors are?  And if they are important?  Should I reload my sources?

Thanks


****
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.bz2:) MD5Sum mismatch
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:) MD5Sum mismatch
[http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Sub-process gzip returned an error code (1)

---

