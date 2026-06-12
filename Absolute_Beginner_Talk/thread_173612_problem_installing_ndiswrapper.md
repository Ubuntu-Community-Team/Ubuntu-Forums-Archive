---
title: "problem installing ndiswrapper"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by jrussel316 on 2006-05-10
I'm completely new to linux, and in trying to install a driver for my wireless card I found out about ndiswrapper.  the problem is when I try to run 'make install' in the ndiswrapper-1.16 directory it gives me the following error:

   can't find kernel build files in /lib/modules/2.6.12-amd64-generic/build;
      give the path to kernel build directory with
      KBUILD=<path> argument to make

it seems my basic problem is that I dont know where my kernel build directory is.  I also tried following the instructions in the ndiswrapper installation guide [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Downloading"), but it seems to me that in the command:

   ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

"/usr/src/linux-<kernel-version>" is supposed to be my kernel build directory, but such a directory does not exist, in fact there is nothing at all in "/usr/src/"

of course I very well may be entirely off my rocker in all of this reasoning.
thanks in advance for your help.

---

### Post by hesser on 2006-05-10
search for the kernel headers for your platform (386, 686, etc) in Synaptic. Install the proper one. Than it will work without the linking.
Did it yesterday.

---

### Post by jrussel316 on 2006-05-10
thanks - that solved the problem i was having, but now it's trying to do the install with gcc-3.4, and i dont have access to that particular version.  I also looked in synaptics and that package wasnt listed there either.  Is there any way to get it to do the compile with gcc-4.0?

---

### Post by macdo on 2006-05-10
Call me stupid, but...

why don't you just install the version of ndiswrapper that's in the repositories? (if you don't have an internet connection on the Ubuntu box, download the deb from [http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils) to your home directory then ```
sudo dpkg -i ndiswrapper-utils
```

The ubuntu package is 1.14, of course.

---

### Post by Sutekh on 2006-05-10
ndiswrapper-utils is also on the Ubuntu Installation CD.

If you still have that you can use it to install ndiswapper-utils
```
sudo apt-cdrom add
```
Then put the Install CD in, then use
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils
```
To install it.

---

### Post by sefs on 2006-05-10
our follow the guide here for installing ndiswrapper....

its a no-brainer

[http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7](http://www.ubuntuforums.org/showthread.php?t=104539&highlight=ndiswrapper+1.7)

---

### Post by jrussel316 on 2006-05-10
oh my goodness that was so ridiculously easy after bashing my head against compiling the thing myself for hours - thank you so much to everyone that's helped me out here - i've never been on anything but windows till yesterday so i'm definitely thankful to have been shown the easy/normal way to install things.

---

