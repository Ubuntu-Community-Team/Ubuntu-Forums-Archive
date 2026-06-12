---
title: "NOOB: can't run the &quot;make&quot; command"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by hashbaz on 2007-07-14
I'm a complete NOOB when it comes to Linux/Ubuntu.  I'm trying to install a NVIDIA driver.  Here is a portion of the instructions :
[quote="instructions"]
You will need to download the NVIDIA FreeBSD Driver Set archives from the NVIDIA website, extract them to a temporary location of your choice, and run the following from the root of the extracted directory:
     % make install
This will compile the.....[/quote]

I have done this (I think - I'm new to all this) but only get an error message.

[quote="terminal"]
loren@spot-II:~$ cd Desktop/temp
loren@spot-II:~/Desktop/temp$ ls -l
total 10972
drwxr-xr-x 2 loren loren     4096 2007-06-24 02:45 junk
drwxr-xr-x 9 loren loren     4096 2007-02-27 00:35 NVIDIA-FreeBSD-x86-1.0-9755
-rw-r--r-- 1 loren loren 11207740 2007-06-09 15:44 NVIDIA-FreeBSD-x86-1.0-9755.tar.gz
loren@spot-II:~/Desktop/temp$ cd NVIDIA-FreeBSD-x86-1.0-9755
loren@spot-II:~/Desktop/temp/NVIDIA-FreeBSD-x86-1.0-9755$ ls -l
total 32
drwxr-xr-x 3 loren loren 4096 2007-02-27 00:35 doc
drwxr-xr-x 8 loren loren 4096 2007-02-27 00:35 lib
-rw-r--r-- 1 loren loren  506 2007-02-27 00:35 Makefile
drwxr-xr-x 2 loren loren 4096 2007-02-27 00:35 mk
drwxr-xr-x 3 loren loren 4096 2007-02-27 00:35 obj
drwxr-xr-x 2 loren loren 4096 2007-02-27 00:35 scripts
drwxr-xr-x 2 loren loren 4096 2007-02-27 00:35 src
drwxr-xr-x 7 loren loren 4096 2007-02-27 00:35 x11
loren@spot-II:~/Desktop/temp/NVIDIA-FreeBSD-x86-1.0-9755$ % make install
bash: fg: %: no such job
loren@spot-II:~/Desktop/temp/NVIDIA-FreeBSD-x86-1.0-9755$ make install
bash: make: command not found
loren@spot-II:~/Desktop/temp/NVIDIA-FreeBSD-x86-1.0-9755$
[/quote]

I've also tried to install a driver for my wireless card and get the same error when I try to execute the "make" command.

What am I doing wrong? and what does " % make install " actually mean?

PS I am running Ubuntu 6.06

---

### Post by FleetAdmiral74 on 2007-07-14
Hmm, there is a package...something like build essential. I bet thats what you need. Its in the repos, I just can't remember exactly what it is.

on second thought, might only be able to get from the command line...

This might help: [http://packages.ubuntu.com/hoary/devel/build-essential](http://packages.ubuntu.com/hoary/devel/build-essential)

---

### Post by Majorix on 2007-07-14
You have to first install the build-essential package.
```
sudo apt-get install build-essential
```

Then configure, compile and install:
```
./configure && make && sudo make install
```

Its not *% make install*, its *sudo make install*.

Also, why do you want to install a FreeBSD package on Ubuntu?

---

### Post by hashbaz on 2007-07-14
> **Majorix said:**
> 
Its not *% make install*, its *sudo make install*.


Is "%" generally used as an abreviation for "sudo"?

> **Majorix said:**
> 
Also, why do you want to install a FreeBSD package on Ubuntu?

Some very simple games will run very poorly on my system so I assume the first place to start is the video driver.  I'm extremely new to Linux - should I not install a FreeBSD package? (not even sure what that means)  This was the only driver I could find for my card.

---

### Post by Majorix on 2007-07-14
I have never heard or seen the use of % as an abbr. for sudo.  So you shouldn't use it as if it was...

And I believe there should be an NVidia driver in the repos. You can use Synaptic (System > Administration > Synaptic Package Manager) to get there. From there, search for nvidia.

I don't have an nvidia card myself, so I can't know for sure, but I believe you will have to run some configuration once you install the driver. Someone here with an nvidia card will help you.

---

### Post by macogw on 2007-07-14
FreeBSD is a different Operating System.  That's like trying to install a Windows driver on a Mac.

---

### Post by Celegorm on 2007-07-14
"%" is not an abbreviation for sudo, rather it's used to mean the command promt. FreeBSD is an entirely different operating system. BSD is a family of unix-like operating systems as is Linux. Given that the driver is not designed for Ubuntu or even Linux, this may cause some problems. As for compiling, ./configure is a command that is used to run a configuration program that is often included with a program's source code, but I don't see configure in the output you posted of ls in the driver's directory. make and sudo make install can be run without using ./configure but more like than not to get it working properly you would have to manually change things in the makefile and that can turn into a real headache even if you already know what you are doing... 

I don't know the proper way to install the restricted nvidia drivers in Ubuntu, but if you click on System -> Preferences -> Desktop Effects, it should prompt you to install the restricted drivers(since you need them in order for desktop effects to work right). I'm guessing the more proper way to get them would be System -> Administration -> Restricted Drivers Manager.

---

