---
title: "[SOLVED] cant play dvd!! not a codec problem!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-19
im trying to play dvds and i have installed medibuntu and the gstreamer thing but i get an error saying "could not read from resource" ???

please help

---

### Post by 1875 on 2008-03-19
Does the disk mount when you put it in your drive? If it does can you open it and browse the content ?

---

### Post by 1875 on 2008-03-19
Also what media player are you using. My guess is Totem. Try VLC if your not already using.

---

### Post by kamitsukai on 2008-03-19
yep i can browse the contents and it wont play in vlc either (T_T)

---

### Post by halitech on 2008-03-19
is this a commercial dvd or one that someone burned? What types of files are showing when you browse the dvd?

---

### Post by 1875 on 2008-03-19
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/117240]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/117240")

[http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/]("http://limulus.wordpress.com/2007/12/10/playing-dvds-in-ubuntu-gutsy/")

Double check its not a codec problem.

---

### Post by kamitsukai on 2008-03-19
> **halitech said:**
> is this a commercial dvd or one that someone burned? What types of files are showing when you browse the dvd?

there all comercial disks and i can see all the vob files and such

---

### Post by kamitsukai on 2008-03-19
ive just searched synaptic but i cant find the package libdvdcss2 its not there!

---

### Post by halitech on 2008-03-19
have you tried using VLC to open one of the vob files to see if it will play?

---

### Post by Tyke91 on 2008-03-19
my hunch is that you didn't properly add the medibuntu repository to your /etc/apt/sources.list file correctly. once you did that, did you get the key as well?

also. if you have done both correctly, then ```
sudo apt-get install libdvdcss2
``` should install it for you

---

### Post by 1875 on 2008-03-19
> **kamitsukai said:**
> ive just searched synaptic but i cant find the package libdvdcss2 its not there!

You will need this if you don't have it. Also it may be illegal for you to use it in certain countries. Try having a lookon the Debian package list, I got mine from a French mirror.

---

### Post by kamitsukai on 2008-03-19
> **1875 said:**
> You will need this if you don't have it. Also it may be illegal for you to use it in certain countries. Try having a lookon the Debian package list, I got mine from a French mirror.

its legal in the uk! and this is what i get when trying to install libdvdcss2 via the terminal

```
carl@carl-desktop:~$ sudo apt-get install libdvdcss2
[sudo] password for carl:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
carl@carl-desktop:~$ 


```

Also does anyone feel like looking at my ndiswrapper wirless problem? LMAO ([http://ubuntuforums.org/showthread.php?p=4547304](http://ubuntuforums.org/showthread.php?p=4547304))

---

### Post by kamitsukai on 2008-03-19
So i assume i havent installed medibuntu right? could someone help to install it properly?

---

### Post by AndyCR on 2008-03-19
Try this in the terminal:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

It should work without having to enable a third-party repository or doing anything else.

---

### Post by 1875 on 2008-03-19
> **kamitsukai said:**
> So i assume i havent installed medibuntu right? could someone help to install it properly?

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by kamitsukai on 2008-03-19
> **AndyCR said:**
> Try this in the terminal:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

It should work without having to enable a third-party repository or doing anything else.

thanks works like a treat! thanks for everyone's help as this has just sorted out all the major problems that i have had with ubuntu and now i'm off to replace the ubuntu theme and install compiz-fusion so wish me luck =)

---

