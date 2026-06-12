---
title: "make/gcc?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by xolot1 on 2006-06-04
i just clean installed dapper yesterday.
now im trying to compile a program.
yet im getting:
```

make: gcc: Command not found
```

make and gcc are installed.
what can i do?

---

### Post by xXx 0wn3d xXx on 2006-06-04
[QUOTE=xolot1]i just clean installed dapper yesterday.
now im trying to compile a program.
yet im getting:
```

make: gcc: Command not found
```

make and gcc are installed.
what can i do?[/QUOTE]
Try:
> sudo apt-get build-essential

---

### Post by xolot1 on 2006-06-04
i thought they build-essential was installed, guess not.

but, build-essential is having a problem:

```
willi@willi-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```





this is my soures.list
```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

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
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free




# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse

```

i didnt see anything wrong with it, can you?

---

### Post by xXx 0wn3d xXx on 2006-06-04
Make sure you have multiverse and universe enabled. Click the "Extra repositories for Dapper/Breezy" in my signature and make sure you have them

---

### Post by aysiu on 2006-06-04
[Build-essential appears to be in the standard repositories.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=build-essential&searchon=name&subword=1&version=all&release=all)

---

