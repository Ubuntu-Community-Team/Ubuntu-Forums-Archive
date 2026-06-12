---
title: "Consistent Error with Various Types of Installation"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by mrphantastic on 2006-09-21
so i am new to forums and to linux, but i am not computer illiterate

my problem is the fact that i have simply been unable to install a variety of things from the "add/remove" package option.

i currently wish to install limewire, and have attempted to do so, but i recieve the following error - about which i am completely lost....

The ERROR is as shown:

havok@havok-desktop:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up cman (1.20060222-0ubuntu5) ...
FATAL: Module cman not found.
 Warning unable to load cman kernel moduleFATAL: Module dlm not found.
 Warning unable to load dlm kernel modulecman_tool: can't open /proc/cluster/status, cman not running
Starting cluster managercman_tool: can't open /proc/cluster/status, cman not running
cman_tool: cannot connect to ccs (name=none)
invoke-rc.d: initscript cman, action "start" failed.
dpkg: error processing cman (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of fence:
 fence depends on cman (= 1.20060222-0ubuntu5); however:
  Package cman is not configured yet.
dpkg: error processing fence (--configure):
 dependency problems - leaving unconfigured
Setting up gulm (1.20060222-0ubuntu5) ...
Starting lock_gulmd:/etc/cluster/cluster.conf was not detected
invoke-rc.d: initscript gulm, action "start" failed.
dpkg: error processing gulm (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of rgmanager:
 rgmanager depends on fence (= 1.20060222-0ubuntu5); however:
  Package fence is not configured yet.
dpkg: error processing rgmanager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clvm:
 clvm depends on cman | gulm; however:
  Package cman is not configured yet.
  Package gulm is not configured yet.
 clvm depends on fence; however:
  Package fence is not configured yet.
dpkg: error processing clvm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on cman; however:
  Package cman is not configured yet.
 redhat-cluster-suite depends on fence; however:
  Package fence is not configured yet.
 redhat-cluster-suite depends on gulm; however:
  Package gulm is not configured yet.
 redhat-cluster-suite depends on rgmanager; however:
  Package rgmanager is not configured yet.
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cman
 fence
 gulm
 rgmanager
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
havok@havok-desktop:~$
         ____________________________________________________

the following:

cman
 fence
 gulm
 rgmanager
 clvm
 redhat-cluster-suite
 system-config-cluster

 - have shown up many times during installation, as errors
          _____________________________________________

my current interest is the fact that this ocurred when i tried to install the "alien" program for the ability to read a certain type of "linux-capable" version of limewire.

does anyone know what in the world i should do?

---

### Post by seshomaru samma on 2006-09-21
I'm by no means an expert , but I would suggest uninstalling alien
Was the installation of alien succesful?
How did you install it?

---

### Post by mrphantastic on 2006-09-21
unfortunately, no, the installation of alien was not successful.  I don't think there is much of anything to uninstall/install until I fix those errors.  I installed it as described by this link:  [http://www.gnutellaforums.com/showthread.php?t=39850](http://www.gnutellaforums.com/showthread.php?t=39850), I just did what "zab" the moderator suggested.  however, those darn errors still popped up... so, I don't know what is next...

---

### Post by mrphantastic on 2006-09-22
does anyone else have any suggestions?  I am just wondering if i am the only one with these kinds of errors, i don't know what they mean/what is causing them...

---

