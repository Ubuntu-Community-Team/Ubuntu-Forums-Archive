---
title: "Really lost."
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by DaveyV on 2007-02-04
Hello all!

I am really new to linux. i am using Kubuntu on my system right now and im having many problems. I try searching but i cant find anything that i can understand,One of my problems is when i enter sudo apt-get update i get this error:
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release)  Unable to find expected entry  multiver$/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: [http://kubuntu.org](http://kubuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

not sure what it is im suppose to do to fix this. Any guides or advice would be GREATLY appreciated! 

I also have problem with my graphic driver I have a 7600GS and i can get it to work? I got many other problems If there is anyone willing to add me on MSN or AIM for instant help i would Thank you!

---

### Post by taurus on 2007-02-04
Open a terminal and edit /etc/apt/sources.list

```
kdesu kate /etc/apt/sources.list
```
and remove the **ca.** from your repos and put a # sign in front of those two repos in there.

```

#deb http://kubuntu.org
#deb http://wine.budgetdedicated.com

```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by DaveyV on 2007-02-04
Thx for reply this is my sources.list:

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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse



i got it from a generator i got it fixed after i entered that into my sources.list

---

### Post by taurus on 2007-02-04
You may want to remove the **us.** from your repos then.

---

### Post by DaveyV on 2007-02-04
Thx alot Taurus got one of many problems settled. Now all i have to tackle is my graphics card problem.

---

### Post by DaveyV on 2007-02-04
Thx alot Taurus got one of many problems settled. Now all i have to tackle is my graphics card problem.

Another quick question wen i get an error like E: Couldn't find package  what should i do or atleast  direct me to good guide for troubleshooting problem dealing with installation via terminal.

---

### Post by taurus on 2007-02-04
> **DaveyV said:**
> Thx alot Taurus got one of many problems settled. Now all i have to tackle is my graphics card problem.

What kind of graphic card do you have?

> Another quick question wen i get an error like E: Couldn't find package  what should i do or atleast  direct me to good guide for troubleshooting problem dealing with installation via terminal.

You probably need more repos in /etc/apt/sources.list.  Make sure you include the dapper repos only, not the edgy since you are using dapper.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by DaveyV on 2007-02-04
Sorry, was out for a bit.

I have a GIGABYTE 7600GS 512MB PCIe card. I enter sudo apt-get install nvidia-glx and afterwards sudo nvidia-glx-config enable and it doesnt work?

---

### Post by taurus on 2007-02-04
Did you look in /etc/X11/xorg.conf to make sure you use "nvidia" driver instead of "nv"?  And did you restart X with <Ctrl><Alt>Backspace?

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by DaveyV on 2007-02-04
No i did not restart with <Ctrl><Alt>Backspace :S

Thx for the website, ima try it now. By any chance Taurus do you have MSN or AIM?

---

