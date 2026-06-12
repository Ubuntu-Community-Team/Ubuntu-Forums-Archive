---
title: "vmware"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by TeLLy_BaN on 2007-08-20
vmware is pissing me off, it keeps trying to install it when im in terminal, regardless of what im doing,  

here i was trying to install amsn.... it asked for my ubuntu CD (why??) and then started installing vmware instead after, 

E: vmware-player: subprocess post-installation script returned error exit status 1

W: Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/pool/main/t/tk8.4/tk8.4_8.4.12-1_i386.deb
 

i also did a sudo get-apt upgrade

and the vmware instal came up, i could paste the whole thing if it helps

I tried removing it,  but it says it dosent exist...

mike@mike-laptop:~$ sudo rm -r /ect/vmware
rm: cannot remove `/ect/vmware': No such file or directory

---

### Post by TeLLy_BaN on 2007-08-20
mike@mike-laptop:~$ sudo apt-get remove --purge vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player libxvidcore4 mplayer-skins libggi2 libgii1 libgii1-target-x
  libxvmc1 liblame0 libfaac0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123382 files and directories currently installed.)
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
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)



any help? I've looked around and saw nothing helpfull

---

### Post by TeLLy_BaN on 2007-08-21
please help???:(...

---

### Post by TeLLy_BaN on 2007-08-21
helppp!!!

---

