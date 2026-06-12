---
title: "VMServer Install Issues"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by shannon.cummins on 2006-08-21
All,
   I have been following the VMWare Server install instructions at [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=wine](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=wine)

The first step gives me this output
```
scummins@alien:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Password:
Reading package lists... Done
Building dependency tree... Done
linux-headers-2.6.15-26-386 is already the newest version.
build-essential is already the newest version.
xinetd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

this is all good, but the next command to install the package results in this.  I have downloaded and checked the file against the MD5 hash, it is good.

```
scummins@alien:~/vmware-server-distrib$ sudo ./vmware-install.pl A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

```

Any ideas or help would be greatly appreciated

---

### Post by David Corrales on 2006-08-21
You probably have the Vmware player installed already. Remove it first! I had tons of trouble because I installed the server then the player simultaneously... only to find out that the free server has a -terrible- lag for GUI stuff (any window redraw is sloooow).
I just downloaded the trial for parallels ([www.parallels.com](www.parallels.com)) and it runs a lot better, only costs $50 and comes in .deb format to boot!

---

### Post by shannon.cummins on 2006-08-21
How did you uninstall it.  I have checked the Synaptics package manager and nothing is installed.  Is there a way to do it from the command line??

---

### Post by djsroknrol on 2006-08-21
Look for a script in one of the directories called vmware-uninstall.pl and run that to uninstall the old version.

---

### Post by shannon.cummins on 2006-08-21
Found the command in both the vmware-server and vmware-player folder.  Executed both, it said successful uninstall.  Still get the error message listed in second code block of my initial post.

---

### Post by djsroknrol on 2006-08-21
I had that issue once as well...I went in and deleted every instance of VMware except the vmware-server-distrib folder and ran the uninstall.pl script again and reinstalled it...you might try that...

---

### Post by David Corrales on 2006-08-22
Yeah, you'll have to delete all traces of Vmware. Remove the packages (will complain of not having any files but will delete them) and the reinstall.

---

### Post by XaeroDegreaz on 2006-08-30
Please read my post here, it solves your problem perfectly.

[http://www.ubuntuforums.org/showthread.php?t=236491&page=2](http://www.ubuntuforums.org/showthread.php?t=236491&page=2)

---

