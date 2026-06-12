---
title: "Ndiswrapper complications!"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-02-17
Nobody wanted to reply to me in Hoary-Hardware & Networking section.  So this is my last resort, since I'm kind of having some time pressure at work.
I've screwed up my Ndiswrapper program in previous attempts at solving a Wifi hardware problem. So I followed this uninstall tutorial the best I could: 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall)
And it seems like removing the user space tools:
'ndiswrapper' (in /usr/sbin) - OK
'loadndisdriver' (in /sbin) - OK
[COLOR="Red"]kernel module 'ndiswrapper' - ERROR[/COLOR]

Here's a snapshot at my attempts to uninstall ndiswrapper and unloading the module, followed by ignoring the ERROR and installing it anyways.

> **guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$** [COLOR="Blue"]sudo make uninstall[/COLOR]
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
[COLOR="Red"]removing /lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper': Is a directory
make: *** [uninstall] Error 1[/COLOR]
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**
> **guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**[COLOR="Blue"] sudo modprobe -r ndiswrapper[/COLOR]
FATAL: Module ndiswrapper not found.
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**
> [B]
guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$[/B][COLOR="Blue"] sudo make install[/COLOR]
make -C driver install
make[1]: Entering directory `/home/guest/Linux/ndiswrapper-1.9/driver'
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/guest/Linux/ndiswrapper-1.9/driver'
make: *** [install] Error 2
**guest@ubuntu-Compis:~/Linux/ndiswrapper-1.9$**
How do I make the fresh installation of Ndiswrapper ERROR free?  Do I also need to uninstall my USB *.inf driver and ndiswrapper-utils before I can make a fresh Ndiswrapper installation.  Because I don't think there's any problem with my *.inf driver and ndis-utils besides I'm gonna use them two later anyways!  What to do, what to do?

---

### Post by jingo811 on 2006-02-21
bump!  Need help please :-k I've reached the end of the world :confused:

---

### Post by kaamos on 2006-02-21
The compile error looks like you wouldn't have headers installed.. Perhaps "sudo apt-get install linux-headers-$(uname -r)" could help.

---

### Post by jingo811 on 2006-02-24
The apt-get Linux header installation sure worked allright.  But it didn't do much difference when trying to sudo make uninstall previous ndiswrapper.

I'm thinking of reinstalling the entire Ubuntu maybe ugrade to Breezy to solve this Wireless problem.  :-k 
What does that Header thingy do anyways?

---

