---
title: "How do I install VMWare 5.5 on Ubuntu 6.06?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by firezip on 2006-06-04
Well I have downloaded the tarball, extracted it, and clicked on the vm-install.pl but when I do nothing happens. Can someone please help me out?

---

### Post by rbalfour on 2006-06-04
> chmod 777 vm-install.pl
> ./vm-install.pl

---

### Post by firezip on 2006-06-04
While installing I get this error

```

Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes]

What is the location of the "make" program on your machine?


```

---

### Post by rbalfour on 2006-06-04
Have you install the kernel sources?
Also what version of vmware? this happen on some 5.5x series.

When I was running 5.10 this is what I did. Check your process with this post
[http://www.vmware.com/community/thread.jspa?threadID=29227&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=29227&tstart=0)

---

### Post by Solver on 2006-06-04
If you are missing make, then you don't have it installed. So you should do

```
sudo apt-get install build-essential
``` to get make and a few other important packages.

---

### Post by firezip on 2006-06-05
I still get this error

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```

I also installed the make

---

### Post by hotstovejer on 2006-06-05
I have a problem with this too. I (by mistake) installed vm player instead of workstation, and now, that I uninstalled player (I think), and I go to run the vmware-install.pl, it gives me this.

A previous installation of VMware software has been detected.

Failure

Execution aborted.

Now I obviously know what this means, I just don't know how to fix it, cause it's not in synaptic.

Any help?

---

### Post by WrathofthePenguin on 2006-06-05
Ok, you need to install the headers (if you haven't already done so), and then put in the correct path to them. I did  this just last week and ran into the same problem. Run this to install the correct headers (cut and paste this exactly - those aren't single quotation marks!):

sudo apt-get install linux-headers-`uname -r` build-essential xinetd

This is the path to the correct directory on my system. It will probably be the same on yours, but you can check it out yourself. Also, if it's not correct you'll get the same error:

/usr/src/linux-headers-2.6.15-23-386/include

Just so everybody knows, my source (although I found the path on my own):

[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)


Good luck!





[QUOTE=firezip]I still get this error

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

```

I also installed the make[/QUOTE]

---

### Post by element on 2006-06-05
WrathofthePenguin - Thanks, that worked for me.

---

### Post by DigitaLink on 2006-06-05
Sweet.  I'm thinking of moving my PCLOS install to K/Ubuntu this summer, but VMWare is an essential app for me.  Good to know I won't have to jump through insane hoops to install it like I've had to on some other distros.  (IE: change kernels, download headers, apply patches, etc etc.)

---

### Post by joshrobinson on 2006-06-05
yeah i ran into the same problem the first time i installed vmware workstation.. i used the same method to fix it, was a pain in the butt at first

---

