---
title: "error message when trying to update"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by malnitz on 2006-09-14
Hi,

I am trying to install the latest update:

linux-image-2.6.15-26-386

... but gets the following error message

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb)
  403 Forbidden

why is this?

- Malnitz

---

### Post by kdnoel on 2006-09-14
I am seeing the same thing here when I try to update... HELP!

It's not really a big deal but just thought everyone would want to know.

I'll try it again later... rights thing or overload is my guess.

---

### Post by Najand on 2006-09-14
Are you guys behind proxy? Are you using gnome or KDE?

---

### Post by HushTheVoices on 2006-09-14
Hi I'm getting exactly the same error.  Being a real newcomer to Ubuntu, I'm a little stuck as to how to fix this.

I'm not going via a proxy and I am using Gnome.

Hope you can help...

---

### Post by Dinerty on 2006-09-14
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

anything to do with this?

---

### Post by Najand on 2006-09-14
> **HushTheVoices said:**
> Hi I'm getting exactly the same error.  Being a real newcomer to Ubuntu, I'm a little stuck as to how to fix this.

I'm not going via a proxy and I am using Gnome.

Hope you can help...

Can you access to the internet without any problem?

---

### Post by kdnoel on 2006-09-14
No proxy and my internet access is working...

---

### Post by Dinerty on 2006-09-14
> **kdnoel said:**
> No proxy and my internet access is working...

you won't be able to get the new kernel as there is a current problem with it ...

---

### Post by kdnoel on 2006-09-14
I have no problem with that I just don't want anybody to freak out!
THanks!:D

---

### Post by Najand on 2006-09-14
Hmm, first of all go and update apt-get using:
```

sudo apt-get update && sudo apt-get upgrade

```
and see if it can refresh your repository package database.

---

### Post by kdnoel on 2006-09-14
Manual update works fine... must be Gnome!
Thanks!

---

### Post by jpick_21 on 2006-09-15
I am seeing the same problem.  I try and update or to use the package manager and get a bunch of connection errors.  I have detailed my problems here running both the gnome and cmd line tools.

[http://www.ubuntuforums.org/search.php?searchid=8198237](http://www.ubuntuforums.org/search.php?searchid=8198237)

If anyone has any idea what is going on I would love to hear it.

---

### Post by Najand on 2006-09-15
> **jpick_21 said:**
> I am seeing the same problem.  I try and update or to use the package manager and get a bunch of connection errors.  I have detailed my problems here running both the gnome and cmd line tools.

[http://www.ubuntuforums.org/search.php?searchid=8198237](http://www.ubuntuforums.org/search.php?searchid=8198237)

If anyone has any idea what is going on I would love to hear it.

Can you copy and paste your error message here?

---

### Post by jpick_21 on 2006-09-15
Sorry, I messed up that link.  Here is the issue:

[http://us.archive.ubuntu.com/ubuntu/...r/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/...r/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...s/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/...s/Release.gpg:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Connection failed [IP: 146.137.96.7 80]
[http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Connection failed [IP: 146.137.96.7 80]

Of course I can hit the URLs in firefox with no problem. Below is my sources.list file. Any help would be greatly appreciated.

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse


I have tried other servces.list files with similar results.  For example

The error

[http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...r/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...r/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/di...y/Release.gpg:](http://security.ubuntu.com/ubuntu/di...y/Release.gpg:) Connection failed
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:](http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:](http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/di...6/Packages.gz:](http://security.ubuntu.com/ubuntu/di...6/Packages.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:](http://security.ubuntu.com/ubuntu/di...ce/Sources.gz:) Connection failed
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:](http://archive.ubuntu.com/ubuntu/dis...6/Packages.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]
[http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:](http://archive.ubuntu.com/ubuntu/dis...ce/Sources.gz:) Connection failed [IP: 195.248.90.23 80]



The file

## Major bug fix updates produced after the final release of the
## distribution.
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
# or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Najand on 2006-09-15
You are behind a proxy server, aren't you?
I like your Alber Einestein Comment... lol

---

### Post by jpick_21 on 2006-09-16
I haven't specified a proxy anyware although maybe I need to?  Right now my browser works and I have things setup to direct connect to the interenet.  I do have a linksys router between the machine and my cable modem, but I didn't think I needed a proxy for that?

I'm glad you like the quote :)

---

### Post by aethernaut on 2006-09-16
this may or may not be related: I can run 'sudo apt-get update' from the command line in my LAMP Server install just fine and dandy...but I'm trying to install something (phpmyadmin) and it keeps locking up on me.

  After building the dependency tree ect it tells me that it will be 24.3mb unpacked and asks if I want to go on...I type "y" and hit enter and it starts....

Then dies...

Screen reads: 75% [working][42949524.660000] hdc: timeout waiting for DMA

and I'm totally locked out: hitting esc does nothing (nor does beating on the keyboard and swearing at the screen; although I find it therapudic to do so). :evil: 

I've used the reset button on my machine 3 times now and it locks up at differant times (first time it was at 99%); but basically the same problem over and over again.

any ideas?

<edit> never mind: I was thinking it was something to do with the download freezing (and so related to the OP's problem); but I'm pretty sure it's a hardware issue now </edit>

---

### Post by jpick_21 on 2006-09-16
I read through the proxy docs to confirm that I should be direct connected and compared my windows network settings to my ubuntu and both are the same.  The only difference is the WINS settings which should be windows specific.

I have also tried ftp from a shell and can download files from the repositories fine that way.  My guess is something is wrong with my authentication or the update program in general.

---

