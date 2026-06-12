---
title: "Can't get anything to apt-get"
date: 2010-01-26
forum: Apple Hardware Users
---

### Post by rlinsurf on 2010-01-26
I finally got my internet working (whew!). So now, I'm trying to install xfsdump. Here's my output:

```
jeffrey@ubuntu-desktop:~$ xfsdump
The program 'xfsdump' is currently not installed.  You can install it by typing:
sudo apt-get install xfsdump
xfsdump: command not found
jeffrey@ubuntu-desktop:~$ sudo -s
[sudo] password for jeffrey: 
root@ubuntu-desktop:~# apt-get install xfsdump
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xfsdump
```
Huh? I typed in exactly what it said... Ok, so then I found this tutorial:

[http://www.howtoforge.com/how-to-build-xfstools-xfsprogs-xfsdump-from-source-on-ubuntu](http://www.howtoforge.com/how-to-build-xfstools-xfsprogs-xfsdump-from-source-on-ubuntu)

Again, here's my output:

```
root@ubuntu-desktop:~# apt-get install git-core libtool libattr1-dev libacl1-dev build-essential automake autoconf uuid-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package git-core
```
Seriously.

Can someone tell me what I'm doing wrong.

---

### Post by linuxopjemac on 2010-01-26
so you have internet, I guess you checked that...

do you have a proper /etc/apt/sources.list ?

---

### Post by howefield on 2010-01-26
Try typing this in your terminal first

```
sudo apt-get update
```

Then try your

```
sudo apt-get install xfsdump
```

---

### Post by rlinsurf on 2010-01-26
I think so. I just got a little farther. I realized I had never done the apt-get update/upgrade, so I did both. Then I was able to run most of the commands.

But I'm now stuck here:

```
# cd ~/xfsdump
# make
# make install
```Here's my output:

```
FATAL ERROR: could not find a valid ncurses header.
Install the ncurses development package.
make: *** [include/builddefs] Error 1
root@ubuntu-desktop:~/xfsdump# apt-get install ncurses
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ncurses is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ncurses has no installation candidate

```??

---

### Post by rlinsurf on 2010-01-26
And farther:

```
apt-get install libncurses5-dev
```

Then tried the make again:

```
FATAL ERROR: cannot find a valid <xfs/xfs.h> header file.
Install or upgrade the XFS development package.
Alternatively, run "make install-dev" from the xfsprogs source.
make: *** [include/builddefs] Error 1
```

Now I am stuck...

---

### Post by rlinsurf on 2010-01-26
nm. Got that too.

Duuuuumb.

Thanks again.

---

