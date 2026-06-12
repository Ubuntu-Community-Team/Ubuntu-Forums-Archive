---
title: "i dont get the compiler"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-05-08
I am a noob, and when I attempt to compile programs (games usually to be on the safe side) it says something like this. (this is when I type ./configure for toy cars-0.0.3 on dapper, many programs have similar results.)

checking for a BSD-compatible install... /usr/bin/iinstall -c
checking whether build enviroment is sane... yes
checking for gawk... no
checking fo mawk... mawk
checking whether make sets $(MAKE)... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See 'config.log' for more details.

I think i am missing a compiler, How do I install one without using some cheap install wizard. I am totally new so please take me through the steps of installing one. (keep in mind the laptop itself is not connected to the internet. but i can download on other computers.) Thank you. I want to become a pro one day, so I want to do it the terminal way.
-Bellinator

---

### Post by Ozeuss on 2007-05-08
first you should install the "build-essential" package through synaptic(or terminal, whatever you prefer). that's a metapackage that contains all you need in order to compile stuff yourself.

---

### Post by Belliinator on 2007-05-08
Does the distro already come with it or do i  download it. I can't see it

---

### Post by Ozeuss on 2007-05-08
in terminal:
```
apt-cache search build-essential
```
will show you the packages realted (no necessary, you just wanted ternminal tools)
```
sudo apt-get install build-essential
```

it should be already enabled in your repositories.

---

### Post by Belliinator on 2007-05-08
Reading package lists... done
Building dependency tree... done
E: Couldn't find package build

Whats with the error.

---

### Post by Ozeuss on 2007-05-08
that's odd. pardon me for my question, but did you type "build-essential" without spaces and with the hyphen?
that package is in Main. you can look it up through synaptic, i'll bet you find it. of course you can also install the packages by writing them down manually- "sudo apt-get install gcc g++ gawk make" and such and such.

---

### Post by jfinkels on 2007-05-08
If you're a beginner, you may want to use Synaptic, the graphical package manager, under "System > Administration > Synaptic Package Manager". Search for "build-essentials", right click on it, and choose to "Mark for installation". Then choose "Apply" from the menu bar at the top of the window, and Synaptic will install the tools you need to compile.

---

### Post by Belliinator on 2007-05-08
Your right Ozeuss, i forgot the hyphen, sorry about that.
However these are the new results.

Reading package lists... Done
Building dependecy tree... Done
Package build-essential is not available, but is referred to by another package. This may mean that the package is missing, has been obseleted, or is only available from another source
E: Package build-essential has no installation candidate

As for synaptic, every time I search for build-essential it comes up with nothing except when I look in dependecies section. It comes up with linux-kernel-devel.

---

### Post by bobplano on 2007-05-08
there's always the seperate parts
```
sudo aptitude install cpp gcc linux-headers-$(uname -r)
```
not really sure if that's all of them though

---

### Post by Belliinator on 2007-05-08
It says:

bellinator@Alture:~$ sudo aptitude install cpp gcc linux-headers-$bellinator -r
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for cpp
No candidate version found for gcc
"linux-headers" is a virtual package provided by:
  linux-headers-2.6.15-26-server-bigiron linux-headers-2.6.15-26-server
  linux-headers-2.6.15-26-k7 linux-headers-2.6.15-26-686
  linux-headers-2.6.15-26-386 linux-headers-2.6.15-26
  linux-headers-2.6.15-25-server-bigiron linux-headers-2.6.15-25-server
  linux-headers-2.6.15-25-k7 linux-headers-2.6.15-25-686
  linux-headers-2.6.15-25-386 linux-headers-2.6.15-25
You must choose one to install.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Did i type it wrong?

---

### Post by Spinelli on 2007-05-08
> **Belliinator said:**
> 
Did i type it wrong?


You probably shouldn't be typing anything. Just copy and paste. Highlight the commands people tell you to use and then middle click in the terminal window. You will never use Ctrl+C and Ctrl+V again. It is one of my favorite features of X11. If you only have two mouse buttons click both at the same time. I would also suggest learning how to use apt-get, apt-cache, and aptitude at the command line before you try compiling software from source.

---

### Post by Belliinator on 2007-05-08
Ok thanks for now.

---

### Post by gerdt on 2007-05-10
sudo apt-get install build-essential 

If he can't find it, you might first have to do an:
sudo apt-get update and perhaps also a sudo apt-get upgrade

if he still can't find it you have to update your /etc/apt/sources.list.
Search this forum for the adequate information on sources.list depending on your distro (dapper/edgy/feisty)

---

### Post by Ek0nomik on 2007-05-10
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install build-essential
```

You should be on your way to greatness.  :)

---

