---
title: "changing repository index?"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by BKK on 2006-06-27
Hello, I was trying to enable all the repositories in Breezy and I am getting this error. I am also getting the similar error when I tried to upgrade to Dapper. I think I need to change where ubuntu looks for updates, i am just not sure where to change.
I get this:
COULD NOT DOWNLOAD ALL REPOSITORY INDEXES
the repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://th.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://th.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://th.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://th.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


I am in Thailand and I assume the th. has to do with that. 
Where can i change and what do i change it too?
 
thanks

---

### Post by halfvolle melk on 2006-06-27
Hi,
The repository list can be found in /etc/apt/sources.list
You can make your own with
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

For instance:
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

---

### Post by BKK on 2006-06-27
Thanks for that adivice. I got a new source file from that source o matic. It fixed some issues, now I get the following error:

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz:) MD5Sum mismatch

Any thoughts? I really dont know what that means, I know that MD5 checks some numbers to make sure files havent been changed

thanks

---

### Post by halfvolle melk on 2006-06-28
Did you try what it says on the top of that page?
> When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)
```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

---

