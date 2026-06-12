---
title: "MacOnLinux install"
date: 2005-05-04
forum: Apple PPC Users
---

### Post by Liakoni on 2005-05-04
Had anyone installed MacOnLinux?
When i triy to run startmol i get this:

root@iBook:/usr/local/mol-0.9.70 # startmol
Mac-on-Linux 0.9.70 [Jan 24 2005 20:08]
Copyright (C) 1997-2004 Samuel Rydh
Starting MOL session 0
Loading Mac-on-Linux kernel module:
FATAL: Module mol not found.
====================================================================
  Failed to load the Mac-on-Linux kernel module -- please install
  mol-modules-source and build your own, or find a binary package
  providing mol-modules for your running kernel.
====================================================================
The mol-modules-source package is installed.

I tried to built it from source but i got errors in make.
Can anyone help with this?

---

### Post by odix on 2005-05-04
Hi, you may find a description [here](http://www.cattlegrid.net/~christophe/titanium/). There is a section on howto install mol, but ignore the rsync parts :-)

regards odiX

---

### Post by ssam on 2005-05-04
have a look at

[Mac On Linux Howto](https://www.ubuntulinux.org/wiki/MacOnLinuxHowto)

---

### Post by Liakoni on 2005-05-04
Thanks, it worked just fine!!!

---

### Post by fidlet on 2005-06-19
I'm also having difficulties getting MOL to work.  I use Hoary, and followed the instructions on the [wiki](https://wiki.ubuntu.com/MacOnLinuxHowto).  Everything went smoothly, until I tried startmol --osx.  I got the error message:

FATAL: Module mol not found.
====================================================================
  Failed to load the Mac-on-Linux kernel module -- please install   
  mol-modules-source and build your own, or find a binary package   
  providing mol-modules for your running kernel.                    
====================================================================

I tried startmol --list:

--------------------------------------------------------------
  Running kernel:         2.6.10-5-powerpc
--------------------------------------------------------------
  Available modules:
    <none>
--------------------------------------------------------------

But, I did install the module per the instructions, synaptic shows that the module is there (for that kernel), and I find the module under /lib/modules.  I've looked at the other posts that cover similar problems but have yet to find anything that can help me (or at least, that I can understand enough to help me: I'm a bit of a newbie).

Any suggestions?

---

### Post by ronin.chitown on 2005-07-16
Ditto here.  

One thing I seem to have trouble with is the headers file.  The path for this does not seem to be set - most docs I read say to run

gedit configure

but it just starts up a new file.  I'm basically trying to set the kernel_path variable to the new header file just in case for some reason the installer didn't do it.  Apart from that, I'm at the old brick wall.  I even tried the Warty hacks on the header out of sheer desperation.

---

### Post by ronin.chitown on 2005-07-16
Update:

Unlike the previous post, I do NOT see MOL in the /lib/modules library.  All that seems to be there are what looks like part of the header files installation.

And, as if you haven't guessed already, I have very little of a clue.  Ubuntu's my first brush with Linux.  On the other hand, I'm in the middle of an article which analyzes how audio apps work with MOL versus that of an old PC.  One of the most annoying things about Apples IMHO is their ridiculous reverse compatibility issues.  I'm hoping that MOL stacks up against my old computer (an old Ti 667 running 9 native) so I can convince others to use it long term.   I'd be happy to share this with the Unbuntu community (for what it's worth) but...first it has to be written!!

Thanks in advance.

---

### Post by ronin.chitown on 2005-07-20
bump!

---

### Post by guidop on 2005-07-29
I had the same problem as fidlet, running hoary on an original iMac233.
I followed the instructions in the wiki for warty, modifying as appropriate,
and got the same "Mol module not found ..." message.

In my case, I looked through my /lib/modules/... directory tree to find the path and name of the mol.ko file and ran the command:

sudo insmod /lib/modules/2.6.10-5-powerpc/misc/mol.ko

starmol now works, with my OS 9.22 booting in a window.

I found this information (and more) at:

[http://www.csse.monash.edu.au/~ctwardy/mol-debian-benh.html](http://www.csse.monash.edu.au/~ctwardy/mol-debian-benh.html)

<http://www.csse.monash.edu.au/~ctwardy/mol-debian-benh.html>

---

### Post by ronin.chitown on 2005-07-31
Forgive the noobness, but whenever I run the command:

bash:/usr/src/modules/mol$ sudo debian/rules build

I get:

 "Nothing to be done for 'build'"

Should I get rid of the old installations to get this working?  I made sure I did the 'apt-get install build-essential' command, and it is up-to-date.

Another thing is that there is no sign of mol.ko - especially in the misc subdirectory.  If anybody has a second, which command does the searching in Ubuntu.  There doesn't seem to be anything on the frontend.

---

### Post by byonk on 2005-08-30
[QUOTE=ronin.chitown]Forgive the noobness, but whenever I run the command:

bash:/usr/src/modules/mol$ sudo debian/rules build

I get:

 "Nothing to be done for 'build'"
[/QUOTE]

I ran into the problem of debian/rules build reporting 'nothing to be done for build' when attempting to repeat the install--it's one of the files in /usr/src/modules/mol resulting in that message i think, I'm not clear which one.

I deleted that directory and was able to follow the wiki instructions from 'sudo debian/rules build' successfully.

however, I still ran into the "FATAL: module mol not found" error; using the insmod command as guidop pointed out solved that.

---

### Post by tomcogley on 2005-09-16
I just got it working ten minutes ago!!   I  had tried this afternoon and I got the same messages about kernel modules not found.  So in synaptic I  removed, completely removed everything associated with mol. I ran apt-get update and then apt-get install for the kernel headers source and kernel. (check synaptic for the specific names that your error messages tell you you need and then close it down so you can run it as apt-get in a root terminal).) I then went through the wiki how-to again from scratch and followed it to a tee.  Use the proper settings in the configuration for your display; its the last step in the how-to.   You may try to start it now.  It won't work...the absolute key is to restart your machine.  Try to have the instructions printed out because you want to be sure to have them so you install the mol program on mac desktop when the mol opens.  Then go back to gnome and do the network configuration.
hope Im of help. T

---

### Post by Deacon Nikolai on 2005-09-17
Unfortunately Mac-On-Linux does not work with "Tiger" Mac OS X 10.4.x  :-(

---

