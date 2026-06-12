---
title: "Repeating Problems"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-11-07
I re-installed Ubuntu to get rid of problems like this:

wesley@wesley-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firestarter (1.0.3-1.1ubuntu4) ...
 * Starting the Firestarter firewall...                                  [fail]
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)

What is going on?

---

### Post by ReaderRat on 2006-11-07
Please don't start another thread when you already have one going...it's considered rude & uncool.

Now, go to System->Administration->Synaptic Package Manager; Enter your password; Click on Search; type in firestarter; In the Packages window, right click on firestarter; click on Mark for Installation; Click on Apply, then wait for SPM to download and install firestarter.
Once it is installed, you can use it to open/close ports, etc.

---

### Post by OptimusPrime on 2006-11-07
Well sorry, I am kind of in a hurry, and this is the script from doing this:
E: firestarter: subprocess post-installation script returned error exit status 2

---

### Post by OptimusPrime on 2006-11-07
I get this when I try to download updates:
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718

---

### Post by OptimusPrime on 2006-11-07
I appologize for my rudeness. :(

---

### Post by ReaderRat on 2006-11-07
KEY Public HowTo get
          **[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)**

---

