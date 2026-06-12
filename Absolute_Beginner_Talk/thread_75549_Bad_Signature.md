---
title: "Bad Signature??"
date: 2005-10-13
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-13
I get this message at the end of sudo apt-get update.

Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

---

### Post by aysiu on 2005-10-13
[QUOTE=nitricacid]You may want to run apt-get update to correct these problems[/QUOTE] Sounds as if it's worth a try.

---

### Post by nitricacid on 2005-10-13
[QUOTE=aysiu]Sounds as if it's worth a try.[/QUOTE]

I do that and it still comes back with the BadSIG.

---

### Post by aysiu on 2005-10-13
How does your /etc/apt/sources.list compare to the appropriate one in here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by nitricacid on 2005-10-13
```
## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051013)]/ breezy main restricted

## All officially supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## deb http://ubuntu.tower-net.de/ubuntu/ hoary java

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## All community supported packages, including security- and other updates
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## The source pacakges
#deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default
deb http://public.planetmirror.com/pub/ubuntu-backports/ breezy-extras main universe multiverse restricted
```

---

### Post by mcpish on 2005-10-20
I'm getting the exact same bad signature error

but when i tried out the new sources file listed here it fixes it.  I think there is something wrong with one of the default security respositories, at least the Canadian one anyhow, here's the message:

> 
W: GPG error: [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


---

### Post by prizrak on 2005-11-16
Hmm this is kinda weird I have the same exact problem on my desktop but not my laptop, they have the same exact apt list file. I also checked what keys I'm using by running sudo apt-key list and they are definetly the same on both machines :(

---

