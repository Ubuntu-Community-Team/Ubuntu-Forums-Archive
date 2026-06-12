---
title: "Aptitude can't load package list"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by seanp2k on 2007-07-14
When I run
```
sudo aptitude update
```

I get the usual scroll then this
```

Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache

```


df -h
```

likwid@pwn3d:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             7.4G  4.7G  2.4G  67% /
varrun                696M  216K  696M   1% /var/run
varlock               696M     0  696M   0% /var/lock
procbususb            696M   88K  696M   1% /proc/bus/usb
udev                  696M   88K  696M   1% /dev
devshm                696M     0  696M   0% /dev/shm
lrm                   696M   33M  663M   5% /lib/modules/2.6.20-16-generic/volatile
/dev/hda1              48G   35G   14G  72% /media/hda1

```

sources.list:
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 


```

dpkg -C
```

Bus error (core dumped)

```

I commented out most of the stuff as it looked either redundant or like it was causing problems.  Thing is, it WAS working and I didn't change sources.list recently.

I did however update automatix through the automatic updates.  Maybe that has something to do with it?

I read a post about MySQL causing problems as well, I use SQlite, a version that is newer than the one in the ubuntu repos.

Also I have ran
```

sudo apt-get update -o APT::Cache-Limit=25165824

```
with the same error (read package list crashes at 7%)

Is there some way to purge the package list and generate a new one?

Thanks.

---

### Post by clitmaster on 2007-07-15
sudo apt-get clean  ....maybe?

---

### Post by seanp2k on 2007-07-15
sudo apt-get clean gives me no output (goes off clean)
then I try sudo apt-get install opera and same problem.

I was thinking maybe if I could reinstall apt?

---

### Post by clitmaster on 2007-07-15
i've no idea then sorry lol

can any1 help this guy?

---

