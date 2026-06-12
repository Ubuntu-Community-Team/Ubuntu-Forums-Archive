---
title: "Data recovery install problems"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by MatthewACT on 2007-05-21
Im using ubuntu.  I need to install data recovery software, can anyone recommend something that reads a hfs(mac) file system?  I've tried to install testdisk, but Ubuntu doesnt recognize the file type.  Can somebody help?

---

### Post by aysiu on 2007-05-21
You might have to install one of these packages: ```
username@ubuntu:~$ *apt-cache search hfs*
genisoimage - Creates ISO-9660 CD-ROM filesystem images
hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
libhfsp-dev - Library to access HFS+ formatted volumes
libhfsp0 - Shared library to access HFS+ formatted volumes
libparted1.7-1 - The GNU Parted disk partitioning shared library
libparted1.7-dbg - The GNU Parted disk partitioning library debug development fi
les
libparted1.7-dev - The GNU Parted disk partitioning library development files
parted - The GNU Parted disk partition resizing program
squashfs-tools - Tool to create and append to squashfs filesystems
basilisk2 - 68k Macintosh emulator
hfsutils-tcltk - Tcl/Tk interfaces for reading and writing Macintosh volumes
libparted1.7-i18n - The GNU Parted disk partitioning library i18n support
lufs-source - Linux Userland Filesystem - kernel module source
lufs-utils - Linux Userland Filesystem - utilities
partimage - backup partitions into a compressed image file
partimage-doc - Partition Image User Documentation
shfs-source - (secure) SHell File System module source
shfs-utils - (secure) SHell File System mount programs
squashfs-source - Source for the squash filesystem
sshfs - filesystem client based on SSH File Transfer Protocol
testdisk - Partition scanner and disk recovery tool
libparted1.6-13 - The GNU Parted disk partitioning shared library
```

---

### Post by MatthewACT on 2007-05-21
install from where?

---

### Post by aysiu on 2007-05-21
> **MatthewACT said:**
> install from where?
Synaptic Package Manager.

More details here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by MatthewACT on 2007-05-21
ok, so I've tried to install testdisk with synaptic and it doesnt show up when I do a search.  When I find it manually, it shows up in gray and I cant select it.  Im starting to think I have a bad version of ubuntu.  I cant download the latest version eith.  It doesnt authenticate, whatever that meANS. Thanks

---

### Post by aysiu on 2007-05-21
It shows up in gray?

Can you post the output of these commands? Just copy and paste the commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then copy and paste back here whatever spits back out at you. ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by MatthewACT on 2007-05-21
should I click on 1 of these links?
I'll try those other 2 commands now

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by MatthewACT on 2007-05-21
how do i set a root password so I can log in as root?

ec@ECcomp:/mnt$ sudo apt-get update
Password:
ec@ECcomp:/mnt$ 
got nothing

---

### Post by aysiu on 2007-05-21
Okay, I see the problem. Testdisk is in the Universe repositories, and you don't have those enabled.

So go back to Synaptic. Go to Settings > Repositories and check off the Universe ones.

Then click Reload, search for *testdisk*, and install it.

If you need any help using Synaptic, go [here](http://www.psychocats.net/ubuntu/synaptic)

---

### Post by aysiu on 2007-05-21
> **MatthewACT said:**
> how do i set a root password so I can log in as root?

ec@ECcomp:/mnt$ sudo apt-get update
Password:
ec@ECcomp:/mnt$ 
got nothing
Oh, that's bad... it just goes to the next line?

You'll have to fix that. [This will help you](http://www.psychocats.net/ubuntu/sudo).

---

