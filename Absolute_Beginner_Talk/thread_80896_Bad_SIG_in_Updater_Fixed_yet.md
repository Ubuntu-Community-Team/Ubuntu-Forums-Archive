---
title: "Bad SIG in Updater Fixed yet?"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-10-23
Just like the title says.

Has the bloody "W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" been fixed yet, or does anyone know how to fix this?!

I Don't know if i am downloading updates or not since nothing ever seems to download.
For those of you that don't have this problem has there been any new updates since the release of Breezy?

---

### Post by rjg1021 on 2006-02-05
Okay, I'm still having this same problem. Is there any known fix? I've switched my /etc/apt/sources.list a bunch of times. Uncommented and recommented. I'm worried that I'm missing out on updates. Please help!

---

### Post by ihristov on 2006-02-15
The solution is the post from **AgenT** at
[http://ubuntuforums.org/showthread.php?t=128602](http://ubuntuforums.org/showthread.php?t=128602)

> 
There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this:

```

# become root
sudo su

# go to apt folder
cd /etc/apt

# Back up current sources.list
cp sources.list sources.list_backup

# make an empty sources.list
> sources.list

# update with your empty repositories list
apt-get update

# revert to saved list
cp sources.list_backup sources.list

# update again and this time you should get no errors
apt-get update 

```


---

