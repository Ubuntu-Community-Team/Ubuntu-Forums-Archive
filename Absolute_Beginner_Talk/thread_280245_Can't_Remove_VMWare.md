---
title: "Can't Remove VMWare"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-10-19
I installed VMWare using Automatix yesterday, but something went horribly wrong *somewhere*. It's mucked up my apt, so I can't install/remove/upgrade anything. Here's what I get when I run *sudo apt-get remove vmware*...

> jo@jo-laptop:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]?
(Reading database ... 89540 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

](*,)

---

### Post by xyz on 2006-10-19
Hi,
I too was not able to remove it using that command line...did it "by hand" and it still shows in Applications > System Tools...

---

### Post by happy-and-lost on 2006-10-19
It wouldn't bother me, but it's mucked up apt-get :(

---

### Post by bulldog on 2006-10-19
There should be a vmware-uninstall.pl in /usr/bin

Can't you remove it with automatix?

---

### Post by xyz on 2006-10-20
You are right bulldog. Thanks. There was about half a dozen vm files in /usr/bin which I deleted as root.
The thing about Automatix is that it says to remove vm running
```
sudo apt-get remove vmware
```
but it doesn't.

---

### Post by xyz on 2006-10-20
Hi happy-and-lost,
Did you by any chance try this:
```
 sudo aptitude purge vmware

```
```
 sudo aptitude purge vmware-player

```

---

### Post by Odisej on 2006-10-29
No, no luck. Tried both commands as I am having the same problem. VMware player is working but I am unable to install anything without it going into some kind of a configuration loop. It is really anoying.

Did not encounter this problem in previous version of Ubuntu.

Odisej

---

### Post by kinematic on 2006-10-29
don't you just love automatix and how it can mess up stuff :p

---

### Post by Kulgan on 2006-10-29
> don't you just love automatix and how it can mess up stuff

yeh, automatix is an **installation** program...

---

### Post by evilhomer on 2006-10-29
i had the same problem.  i solved it by installing the .tar'd version of vmware from vmware.com.

tar -xvf VMware*
cd vmware*
sudo ./vmware-install.pl

that allowed me to apt-get remove it:

sudo apt-get remove vmware*

then i did the uninstall command on the .tar'd version.:
cd bin
sudo ./vmware-uninstall.pl

---

### Post by Kulgan on 2006-10-29
just ./vmware-uninstall.pl did it for me :D

---

### Post by tictactatic on 2006-12-04
Thanks guys, it worked for me.

Just a note for those who follow the suggested procedure: do not configure the vnet options when installing vmware-player from source. The default option there is yes, so if you are quick on the enter key, you are in for trouble. ;)

---

