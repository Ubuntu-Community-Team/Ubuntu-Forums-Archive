---
title: "Fiesty upgrade failed."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Repent on 2007-04-20
after spending 9 hrs downloading I get this.

[IMG]http://i16.tinypic.com/2gwck1y.png[/IMG]

So I think maybe I will try again so I fire up the Synaptic Package Manager and I get this.

[IMG]http://i18.tinypic.com/40fvqdl.png[/IMG]

So I run 'sudo apt-get install -f ' and this is what I get.

joe203@joe203-desktop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  airstrike-common apache2-common mozilla-firefox
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apache2-mpm-prefork apache2.2-common
The following packages will be REMOVED:
  apache2-common
The following NEW packages will be installed:
  apache2.2-common
The following packages will be upgraded:
  apache2-mpm-prefork
1 upgraded, 1 newly installed, 1 to remove and 1004 not upgraded.
2 not fully installed or removed.
Need to get 128kB/1486kB of archives.
After unpacking 602kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe havp 0.79-1 [128kB]
Fetched 128kB in 4m39s (457B/s)
(Reading database ... 159722 files and directories currently installed.)
Preparing to replace havp 0.79-1 (using .../archives/havp_0.79-1_i386.deb) ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/havp_0.79-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-CKNJgc: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/havp_0.79-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
joe203@joe203-desktop:~$ 

joe203@joe203-desktop:~$ 

Someone please help!

---

### Post by weijie90 on 2007-04-20
This may help.

[http://ubuntuforums.org/showthread.php?t=346454](http://ubuntuforums.org/showthread.php?t=346454)

---

### Post by Repent on 2007-04-20
Thank you that worked but now I get this and still no upgrade.:( 

Could not install '/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

subprocess pre-installation script returned error exit status 2

How can I fix this?

---

### Post by syukton on 2007-04-22
I'm having almost the exact same problem. I get a dialog that says this:

> Could not install '/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

subprocess pre-installation script returned error exit status 2

Then when I dismiss that dialog, I get this one:

> The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

I'm running Kubuntu 6.10, if that matters. Any ideas? It seems to be directly related to installing the new nvidia driver...

Edit: I ran ** sudo apt-get install -f** and it didn't say anything about havp; this is the output:
> 
syukton@tundra:~$ sudo apt-get install -f

Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libarts1c2a libesd-alsa0 libopenexr2c2a
Recommended packages:
  esound-clients
The following packages will be upgraded:
  libarts1c2a libesd-alsa0 libopenexr2c2a
3 upgraded, 0 newly installed, 0 to remove and 1101 not upgraded.
4 not fully installed or removed.
Need to get 0B/1321kB of archives.
After unpacking 213kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 168442 files and directories currently installed.)
Preparing to replace libarts1c2a 1.5.4-0ubuntu1 (using .../libarts1c2a_1.5.6-0ubuntu1_i386.deb) ...
Unpacking replacement libarts1c2a ...
Preparing to replace libesd-alsa0 0.2.36-3ubuntu3 (using .../libesd-alsa0_0.2.36-3ubuntu4_i386.deb) ...
Unpacking replacement libesd-alsa0 ...
Preparing to replace libopenexr2c2a 1.2.2-4.3 (using .../libopenexr2c2a_1.2.2-4.3ubuntu1_i386.deb) ...
Unpacking replacement libopenexr2c2a ...
Setting up libesd-alsa0 (0.2.36-3ubuntu4) ...

Setting up libesd0-dev (0.2.36-3ubuntu4) ...
Setting up libarts1c2a (1.5.6-0ubuntu1) ...

Setting up libarts1-dev (1.5.6-0ubuntu1) ...
Setting up libopenexr2c2a (1.2.2-4.3ubuntu1) ...

Setting up libopenexr-dev (1.2.2-4.3ubuntu1) ...

Setting up kdelibs4-dev (3.5.6-0ubuntu14) ...
syukton@tundra:~$

I was able to run Update Manager again, but I just got the same error as I initially received. This is really annoying, it happens 8 minutes from completion every time!

Edit: The third or fourth time it happened, install continued and everything turned out alright. So, uh, persistence pays off, or something.

---

