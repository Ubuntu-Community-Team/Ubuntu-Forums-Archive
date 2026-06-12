---
title: "Real Player"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-01-16
Hello
I want to be able to install real player, its not in the syptmatic source.....
when i go to the realplayer site [http://www.real.com/linux](http://www.real.com/linux) and u download doesnt do anything.....

so i found this website [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/) 
I can download both .bin and rpm, but i cant seem to install either of them
Please could someone tell me how to

I have download them to the desktop
the file names are
HelixPlayer-1.0.9.816-20070818.i586.rpm
RealPlayer-10.0.9.809-20070726.i586.rpm
hxplay-1.0.9.816-linux-2.2-libc6-gcc32-i586.bin
realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

I dont need all of them install preferable the real player version, but as long as the bbc website plays audio again i will be happy!

---

### Post by lgambett on 2008-01-16
None of the above... Downolad trhe .deb package from here on your desktop
[http://www.debian-multimedia.org/pool/main/r/realplay/](http://www.debian-multimedia.org/pool/main/r/realplay/)
then double click on it. It should work flawlessly.
Although it is possible to install a RPM over an Ubuntu Linux, it is always better to search first for the Debian package (.deb).

---

### Post by ibizatunes on 2008-01-16
Only one prob with that Im a x64 user..... (god dam creative xfi 64 bit drivers only)
[http://ubuntuforums.org/showthread.php?t=598355](http://ubuntuforums.org/showthread.php?t=598355) Say it can be done
But the have to compile it from the command line, and as im a new to linux its a bit tricky!!

---

### Post by lgambett on 2008-01-16
There is nothing to compile, the .tar.gz contains a binary setup file.
1) download the .tar.gz from the website I mentioned in the previous post
2) open a terminal
3) give the execution permission to the binary file with the chmod a+x command
4) execute the binary file

The process is described also in the link that you have posted.
Good luck !

---

### Post by lgambett on 2008-01-16
Sorry, I forgot; untar the tar.gz after having downloaded with
tar -xvzf <filename>. 

You can also follow the istructions there;
[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by SOULRiDER on 2008-01-16
Check this out
[http://ubuntuforums.org/showthread.php?t=587953](http://ubuntuforums.org/showthread.php?t=587953)

The second post explains how to install RealPlayer form the repos.

---

