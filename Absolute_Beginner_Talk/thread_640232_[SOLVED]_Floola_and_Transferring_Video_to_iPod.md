---
title: "[SOLVED] Floola and Transferring Video to iPod"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by blurryone on 2007-12-13
Hi All,

I am running x64bit version of Ubuntu, and i cannot open Floola (technically i can it just doesn't stay open for more than 1 sec).

According to the website i need some libs from the 32bit version of Ubuntu however the link on the Floola site is no longer working... Just wondering if anybody has this going on 64bit and what they used to get it working.

Here are the error messages and supporting links..


Error Msg

xxxxx@xxxxxxxxx:~$ '/home/xxxxx/Desktop/Floola-linux/Floola' 
Cannot find libgstreamer
Cannot find libxine
Segmentation fault (core dumped)
^^^application exits here


Out of the Floola FAQ

I'm running a x64 linux distro and Floola doesn't work

You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1). If you don't know how to do this simply copy as root files contained in [this]("http://www.pochoirs.de/files/32bit_libs.rar") package to /usr/lib32 (Thanks Adam Thayer)

^^^^ Link doesn't work any more...

Any help would be greatly appreciated!!! I will also try advising the webmaster of the floola site about the dead link.

Cheers All

Blurry:confused:

---

### Post by Incense on 2007-12-14
Try running the windows version of floola under wine. You may have a better chance of getting it to work that way.

---

### Post by blurryone on 2007-12-14
Already tried that it says it doesn't detect the iPod

---

### Post by Incense on 2007-12-14
That's no good then. I had it work on a 32 bit system before, but I guess that's a no go on 64. Sorry mate, I tried. Hope someone has some better info for ya. Good luck.

---

### Post by blurryone on 2007-12-14
Cheers mate, appreciate it. I hope so too...

still nothing from floola forums etc

Blurry
:popcorn:

---

### Post by blurryone on 2007-12-15
Still nothing from the blokes at floola. i can not be the only one with an ipod and a 64bit machine can i??

hello....

anybody.....

hehe but seriously..

---

### Post by blurryone on 2007-12-17
sweet... the webmaster fixed the link.... here it is guys

_____________________________________________________________

I'm running a x64 linux distro and Floola doesn't work

You'll need to have proper 32bit version of some libraries (libcups, libgcrypt, libgnutls, libgpg-error, libtasn1). If you don't know how to do this simply copy as root files contained in [this]("http://www.floola.com/download/click.php?action=go&to=32bitlib-lin") package to /usr/lib32 (Thanks Adam Thayer)

____________________________________________________________

:guitar::guitar:

---

### Post by eznet on 2008-05-21
Don't know about you, but even with the provided files in my 32 bit library, Floola will not load...

---

