---
title: "Puppy Linux - Intel Gigabit Card Drivers"
date: 2013-02-07
forum: Any Other OS
---

### Post by rodmiles on 2013-02-07
Hi Everyone,

I currently have a Lenovo Desktop PC running Ubuntu 12.04 LTS which works like a dream. I also have a bootable USB drive running Puppy Linux which appears to be working just fine when I boot into it except for the network card (which works no problem with Ubuntu).

The network card is an *Intel 82567LM-3 Gigabit Network Card rev 02*. I have attempted to install the module manually from the list available which looks to include quite a few Intel modules for the Intel cards. None of which manage to detect the network card once loaded.

I ran the 'ifconfig' command and it only shows up the 'lo' adaptor and no eth0 interface. I even tried 'ifconfig eth0 up' but still with no luck.

I have downloaded the Linux tar.gz driver file from the Intel support page, however, that is where my limited knowledge of installing the package now ends. Could someone please explain to me how to now install the package in Puppy so that I can get my network card working?

I looked through the readme.txt file that comes with the driver package and it does describe the method of how to "build" the file. I am not sure what the information means and I'm hoping there is a more simplified way to install this package than my mind has pictured at the moment?

Many thanks for your help and advice in advance.

---

### Post by UltimateCat on 2013-02-10
Hi:

You can use the Puppy Manager to install the driver inside the tar.gz

If the .tar.gz file are not puppy linux approved they could cause serious instability to your system.
 
See this page it should help you to understand a tar.gz and the how to part-

[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)

[http://askubuntu.com/questions/191390/how-to-use-sudo-command-to-install-tar-gz](http://askubuntu.com/questions/191390/how-to-use-sudo-command-to-install-tar-gz)
[http://puppylinux.org/wikka/ppm](http://puppylinux.org/wikka/ppm)

It's a good idea to check the integrity of a file after you download it. This article helps. The in-built [MD5sum]("http://puppylinux.org/wikka/MD5sum") is handy, as the file can be checked for integrity after being downloaded.
[http://puppylinux.org/wikka/Pets](http://puppylinux.org/wikka/Pets)

Hope this helps

---

