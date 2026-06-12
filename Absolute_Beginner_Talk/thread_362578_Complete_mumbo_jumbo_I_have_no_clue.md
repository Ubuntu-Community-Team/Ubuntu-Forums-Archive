---
title: "Complete mumbo jumbo I have no clue"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by speeddemon8803 on 2007-02-15
robb@robb-laptop:~$ sudo aptitude remove rageircd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  rageircd 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1544kB will be freed.
Writing extended state information... Done
(Reading database ... 191856 files and directories currently installed.)
Removing rageircd ...
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "stop" failed.
dpkg: error processing rageircd (--remove):
 subprocess pre-removal script returned error exit status 1
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ggz-grubby (0.0.13-2ubuntu1) ...
/var/lib/dpkg/info/ggz-grubby.postinst: 3: ggz-config: not found
dpkg: error processing ggz-grubby (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ggz-grubby

Its not in my synaptics or even my Add/Remove applications...I dont feel like re-formatting my computer for the 12th time just because of this so ANY help in resolving this problem would be great!

---

### Post by dcstar on 2007-02-15
> **speeddemon8803 said:**
> robb@robb-laptop:~$ sudo aptitude remove rageircd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  rageircd 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1544kB will be freed.
Writing extended state information... Done
(Reading database ... 191856 files and directories currently installed.)
Removing rageircd ...
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "stop" failed.
dpkg: error processing rageircd (--remove):
 subprocess pre-removal script returned error exit status 1
ERR: Not starting Rage IRC Daemon: unconfigured package. Edit /etc/rageircd/rageircd.conf
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ggz-grubby (0.0.13-2ubuntu1) ...
/var/lib/dpkg/info/ggz-grubby.postinst: 3: ggz-config: not found
dpkg: error processing ggz-grubby (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 ggz-grubby

Its not in my synaptics or even my Add/Remove applications...I dont feel like re-formatting my computer for the 12th time just because of this so ANY help in resolving this problem would be great!

Try:
```
sudo dpkg-reconfigure rageircd
```
The if that goes ok, try to remove it with your other command.

---

### Post by speeddemon8803 on 2007-02-16
root@robb-laptop:~# sudo dpkg-reconfigure rageircd
/usr/sbin/dpkg-reconfigure: rageircd is broken or not fully installed
root@robb-laptop:~#

---

### Post by jordanmthomas on 2007-02-16
```
sudo apt-get -f install
```
see if that helps.  It is supposed to fix broken stuff

---

### Post by go2dell on 2007-02-16
It appears this was corrected upstream (in Debian), but the [bug report]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=369825") there might help you to fix the problem right now.  In my admittedly cursory glance at the problem, it appears that it's simply not removing the user directory, so removing it by hand would correct the problem.  You shouldn't need to reinstall at all.

Maybe you should file a [bug report]("https://launchpad.net/ubuntu/+source/rageircd/+filebug") for Ubuntu?

---

