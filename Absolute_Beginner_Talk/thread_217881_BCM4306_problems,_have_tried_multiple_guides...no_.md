---
title: "BCM4306 problems, have tried multiple guides...no luck so far."
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-07-17
Posting here because I've had not much luck getting help in the Wireless Support Forum

Here's what I've tried most recently:

jackfrost@jackfrost-laptop:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found.
jackfrost@jackfrost-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
jackfrost@jackfrost-laptop:~$ sudo apt-get remove ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ndiswrapper-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 79459 files and directories currently installed.)
Removing ndiswrapper-utils ...
dpkg - warning: while removing ndiswrapper-utils, directory `/etc/ndiswrapper' not empty so not removed.
jackfrost@jackfrost-laptop:~$ sudo rm -r /etc/ndiswrapper/
jackfrost@jackfrost-laptop:~$ sudo rm -r/etc/modprobe.d/ndiswrapper
rm: invalid option -- /
Try `rm --help' for more information.
jackfrost@jackfrost-laptop:~$ sudo rm -r /etc/modprobe.d/ndiswrapper
jackfrost@jackfrost-laptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6kB of archives.
After unpacking 139kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ndiswrapper-utils 1.8-0ubuntu2 [27.6kB]
Fetched 27.6kB in 0s (28.5kB/s)
Selecting previously deselected package ndiswrapper-utils.
(Reading database ... 79447 files and directories currently installed.)
Unpacking ndiswrapper-utils (from .../ndiswrapper-utils_1.8-0ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...

jackfrost@jackfrost-laptop:~$ sudo ndiswrapper -i ~/home/jackfrost/Desktop/bcmstuff/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/jackfrost/home/jackfrost/Desktop/bcmstuff/bcmwl5.inf at /usr/sbin/ndiswrapper line 135.
jackfrost@jackfrost-laptop:~$ sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
jackfrost@jackfrost-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/*.conf: Permission denied
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
jackfrost@jackfrost-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; > done
bash: syntax error near unexpected token `done'
jackfrost@jackfrost-laptop:~$ for $conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile; done
bash: `$conffile': not a valid identifier
jackfrost@jackfrost-laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile; done
bash: /etc/ndiswrapper/bcmwl5/*.conf: Permission denied
cat: /etc/ndiswrapper/bcmwl5/*.conf: No such file or directory
jackfrost@jackfrost-laptop:~$

---

### Post by Jagot on 2006-07-17
Don't know if this will be of any use to you, but I have a Broadcom 4318 and this is how I do it:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

The first section actually installs the driver.  The second section blacklists the built-in Broadcom drivers in Ubuntu (which don't work for me).

Then it's just a matter of configuring the network settings.

---

### Post by UberIcarus on 2006-07-17
This is what I get when I try that:

jackfrost@jackfrost-laptop:~$ sudo ndiswrapper -i ~/home/jackfrost/Desktop/bcmwl5.inf
Installing bcmwl5
couldn't copy /home/jackfrost/home/jackfrost/Desktop/bcmwl5.inf at /usr/sbin/ndiswrapper line 135.
jackfrost@jackfrost-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
jackfrost@jackfrost-laptop:~$  sudo ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
jackfrost@jackfrost-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a/etc/modprobe.d/blacklist
tee: invalid option -- /
Try `tee --help' for more information.
jackfrost@jackfrost-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
jackfrost@jackfrost-laptop:~$ sudo rmmod bcm43xx
ERROR: Module bcm43xx does not exist in /proc/modules
jackfrost@jackfrost-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
jackfrost@jackfrost-laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
jackfrost@jackfrost-laptop:~$

---

### Post by UberIcarus on 2006-07-18
Bump.

---

