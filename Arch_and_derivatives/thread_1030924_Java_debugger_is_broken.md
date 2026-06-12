---
title: "Java debugger is broken"
date: 2009-01-04
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2009-01-04
I'm running latest Arch (pacman -Syu) and openjdk6.  In both Netbeans and jgrasp IDEs, the debugger does not work.  I get a transport error 202: connection refused message when I try to debug.  I've tried installing Sun's jdk, but I get the same error.  java, javac, and jdb are all symlinked in /usr/bin (which is in my $PATH); I thought this might be a problem, so I added the actual directory of each of those binarys to the beginning of the path (so that it is checked before /usr/bin), but that didn't seem to do any good.

Any idea what I could be doing wrong?  I had the debugger working on an old install of Arch as well as Ubuntu 8.10... I don't know what I could have done to bork it.

---

### Post by crimesaucer on 2009-01-05
> **TheOrangePeanut said:**
> I'm running latest Arch (pacman -Syu) and openjdk6.  In both Netbeans and jgrasp IDEs, the debugger does not work.  I get a transport error 202: connection refused message when I try to debug.  I've tried installing Sun's jdk, but I get the same error.  java, javac, and jdb are all symlinked in /usr/bin (which is in my $PATH); I thought this might be a problem, so I added the actual directory of each of those binarys to the beginning of the path (so that it is checked before /usr/bin), but that didn't seem to do any good.

Any idea what I could be doing wrong?  I had the debugger working on an old install of Arch as well as Ubuntu 8.10... I don't know what I could have done to bork it.


This isn't really a solution but more of a suggestion if you are on "x86_64": [http://aur.archlinux.org/packages.php?ID=22264](http://aur.archlinux.org/packages.php?ID=22264)


I had been using OpenJDK6 and the Iceadtea plugin and was basically happy with it for Arch64. Then after Sun Java started to support 64bit I un-installed the "openjdk6" package and then installed the AUR "jre_beta 6u12_b03-1" package..... 


Now I was finally able to use Photobucket.com's java applet for bulk uploading.

---

