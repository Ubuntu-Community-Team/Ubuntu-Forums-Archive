---
title: "Questions/Problems w/ apt-get update and synaptic"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by FadedPosterChild on 2005-06-04
Hello, I've been using ubuntu for about 3 days, and this is my first linux distro ever so I am completely lost. I keep getting the following errors:

when using:  apt-get install mplayer-386

I get: 

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to  be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be in stalled
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

I've tried updateing with apt-get update; but then i get this:


W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
root@Faded:/home/fadedposterchild #

Any help would be greatly appreciated

---

### Post by poofyhairguy on 2005-06-04
> **FadedPosterChild]Hello, I've been using ubuntu for about 3 days, and this is my first linux distro ever so I am completely lost. I keep getting the following errors:

when using:  apt-get install mplayer-386

I get: 

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to  be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be in stalled
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

I've tried updateing with apt-get update said:**
> http://us.archive.ubuntu.com[/url] hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
root@Faded:/home/fadedposterchild #

Any help would be greatly appreciated


Ok. Two things. First of all, Not having a public key isn't a bad thing. Our backports repo lacks it, its ok. Nothing is wrong, apt-get is picky.

Secondly (and much more importantly) this shows me that you have  Marillat Repository added. This is what is causing this problem.

Open up a terminal. Enter in this command:

gksudo gedit /etc/apt/sources.list

When the file comes up look for lines the go:

>  deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main 

If you see any of these, delete them. Add these lines instead:

> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

Now save the file and exit. Enter this command:

sudo apt-get update

Then (it will still give you key errors, ignore these) do

apt-get install mplayer-386

If you want. Personally I think both Gxine and VLC work better.

sudo apt-get install gxine gvlc

try them all and see what you like. Good luck.

---

### Post by ubuntulnx on 2005-06-18
hi.. ive been continuesly upgrading all security upgrades. some time ago the marillat debs did not work anymore for me. that part was answered already. but after make the suggested changes, somehow ubuntu want me to install updates for below packages..

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
The following packages will be upgraded:
  file-roller foomatic-db-hpijs foomatic-filters-ppds gaim gaim-data gimp
  gimp-data gimp-python gnome-btdownload gnome-menus hpijs libgcc1 libgimp2.0
  libgnome-menu0 libnspr4 libnss3 libsmbclient python-xdg python2.3-samba
  python2.4-samba samba-common smbclient synaptic totem totem-xine xchat
  xchat-common
27 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 42.6MB of archives.
After unpacking 2140kB of additional disk space will be used.
Do you want to continue [Y/n]?

why is that? and what harm could i do going ahead with the update? and what happens if i eliminate both marillat and backports? i think i only installed the gstreamer-mad package from marillat. THANKS.

---

### Post by Mez on 2005-06-18
> **FadedPosterChild]Hello, I've been using ubuntu for about 3 days, and this is my first linux distro ever so I am completely lost. I keep getting the following errors:

when using:  apt-get install mplayer-386

I get: 

The following packages have unmet dependencies:
  mplayer-386: Depends: libavcodeccvs (>= 2:20050417-0.0) but it is not going to  be installed
               Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be in stalled
               Depends: libpostproc0 (>= 2:20050417-0.0) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
               Depends: xmms (>= 1.2.10+cvs20050209) but 1.2.10-2ubuntu1 is to be installed
E: Broken packages

I've tried updateing with apt-get update said:**
> http://us.archive.ubuntu.com[/url] hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
root@Faded:/home/fadedposterchild #

Any help would be greatly appreciated
 In reply tot eh first post, us.archive.ubuntu.com is currently experiencing problems, run the command

```
sudo sed -e 's/us.archive/archive/' -i /etc/apt/sources.list
``` 

then 
```
sudo apt-get update
```

to fix this problem (you may have to run it a few times if you keep having probelms

---

### Post by robertobech on 2005-07-06
It worked! What exactly does this command do?

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=robertobech]It worked! What exactly does this command do?[/QUOTE]


sudo apt-get update tells the apt-get program to update itself and take notice of changes you made. Its kinda like a safety on a gun....

---

