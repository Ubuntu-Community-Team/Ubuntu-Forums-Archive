---
title: "BCM94306 ndis wrapper with no internet"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by theweakend on 2007-05-30
Ok here is the scenario I have a win/feisty dual boot the win obviously has internet and the feisty doesn't but I do have a external hard drive as my "os share" [this]("http://ubuntuforums.org/showthread.php?t=201902") is a rather definitive guide yet it really doesn't take into account that you may not have a wired modem I know there is a way to do it but how?

---

### Post by NICU on 2007-05-30
The easiest way to do this is by using a USB thumb drive.  Fill it up with all the source for ndiswrapper (if its not installed by default), also copy the Windows drivers for your WiFi card to the thumb drive.  Linux can mount the thumb drives easily and that should allow you to do whatever you need.  If you don't have a thumb drive try to burn a CD with the source and drivers.  Let me know if that helps, or if I'm not answering your questions.  Good luck

---

### Post by theweakend on 2007-05-31
Basically what I am asking is how to I "sudo aptitude install linux-headers-2.6.17-10-generic" when I have no internet?

---

### Post by NICU on 2007-05-31
You can find the package for Linux-Headers-2.6.20-15-generic (current Fiesty kernel) at [http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-15-generic](http://packages.ubuntu.com/feisty/devel/linux-headers-2.6.20-15-generic)  Download the .deb file from any mirror listed [here.]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fl%2Flinux-source-2.6.20%2Flinux-headers-2.6.20-15-generic_2.6.20-15.27_i386.deb&md5sum=510cbf1efb528a0322690009cdb9d233&arch=i386&type=main")

As I said in a previous post, the easiest way to transfer these files to your Ubuntu install is by using a CD-R or USB thumb drive.  Add the .deb file you just downloaded to the CD/thumb drive.  Then install the .deb file by using this [simple tutorial]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install.2Funinstall_.deb_files") 

After that go ahead and install ndiswrapper, locate your .inf file from the Windows XP driver and setup your WiFi card.  Please update us on your progress.

*Edit - The current kernel is 2.6.20-15, not 2.6.17-10 like the tutorial says, you can type "uname -r" in a terminal to see what your kernel version is, if you're using feisty it should be 2.6.20-15 and you will want to follow all the instructions I gave you above. Its its not please tell me what numbers you get back from uname -r.

---

### Post by theweakend on 2007-05-31
Well it turns out that I also need "build-essential" easy enough I downloaded it and put it on my external well to install "build-essential" i also need "g++" yep I got that too. Then "g++" needs "g++-4.1" I installed that and then "g++" also needs "libstdc++6-4.1-dev" I tried to install that but it requires "g++-4.1" but didn't that require "libstdc++6-4.1-dev"? so I am guessing I have to force an install but I am not sure how to do that any ideas?

---

### Post by Bachstelze on 2007-05-31
Why bother ? Both the headers and build-essential are on your Ubuntu CD.

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add
*** insert CD here and press enter ***
sudo apt-get update
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by theweakend on 2007-05-31
Really god I really feel stupid now lol

Lets try this again, but the smart way this time...

*EDIT* After following HymnToLife's little help everything went fine up until I bring up firefox and enter random word into the google search and nothing

any idea how to trouble shoot this? There were no compile errors and I *think* I am using the right drivers (I am running 64 bit ubuntu with 64 bit drivers from linuxant). 

thanks for being so patient and helping me.

---

