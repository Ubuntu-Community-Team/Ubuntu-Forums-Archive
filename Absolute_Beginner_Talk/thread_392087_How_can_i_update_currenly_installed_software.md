---
title: "How can i update currenly installed software"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2007-03-24
How can i update  currenly installed software?

Like amsn or gtk-gnutella 

i installed them through synaptic

---

### Post by xopher on 2007-03-24
Synaptic takes care of this automatically, if there's an updated version available in the repositories.

```
sudo apt-get update; sudo apt-get upgrade
```

If the latest one isn't in the official repositories yet, there might be a 3rd-party one that has it. Be sure to check out the backports-project ;)

Now, if you for some reason need to be on the bleeding edge all the time, then compiling the software yourself is an option, but then ubuntu isn't your distro, try gentoo instead..

---

### Post by fasoulas on 2007-03-24
:~$ sudo apt-get update; sudo apt-get upgrade
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
**99% [Connecting to cy.archive.ubuntu.com (91.189.89.6)] [Connecting to archive.**

It stays there and it doesn't check them all 
also everything i try to install by typing :
sudo aptitude or sudo apt-get also stays there

and about the software:
gtk-gnutella doesn't open because a new version came out one of my friends has the same problem

---

### Post by seshomaru samma on 2007-03-24
try using a mirror
go to[ this site ]("http://www.ubuntu-nl.org/source-o-matic/")
generate a new source list 
then:
```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```
and
```
sudo gedit /etc/apt/sources.list
```
replace everything with the new sources you've generates and run 
```
sudo apt-get update
```
again

---

### Post by fasoulas on 2007-03-24
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://cy.archive.ubuntu.com/ubuntu](http://cy.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://cy.archive.ubuntu.com/ubuntu](http://cy.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://cy.archive.ubuntu.com/ubuntu](http://cy.archive.ubuntu.com/ubuntu) dapper universe multiverse 
deb [http://cy.archive.ubuntu.com/ubuntu](http://cy.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://cy.archive.ubuntu.com/ubuntu](http://cy.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse 

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial main 

this is my sources file
but i still have the same problem

---

### Post by zanglang on 2007-03-24
The mirror for your country might be having network problems causing your updates to stall, so try selecting a nearby country in the sources.list generator, and then run apt-get update again.

---

### Post by fasoulas on 2007-03-24
> **zanglang said:**
> The mirror for your country might be having network problems causing your updates to stall, so try selecting a nearby country in the sources.list generator, and then run apt-get update again.

Thnx that was the problem and now it is solved\\:D/

---

