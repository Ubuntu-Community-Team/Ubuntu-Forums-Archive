---
title: "Trying to remove VMWare Player"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by aristotlewilde on 2006-10-25
I am getting the following error when trying to "sudo apt-get remove vmware-player"

> scott@scott-desktop:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158409 files and directories currently installed.)
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
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone help me out here?

I accidentally installed vmware server and vmware player and want to remove the player.  I am running Ubuntu 6.06 x86.

---

### Post by l33tbuntuhax0r on 2006-10-25
[SIZE="4"][FONT="Fixedsys"][COLOR="Red"]un!n$7411 8y h4nd

```
cd /
find . | grep vmware
rm -rf /path/to/vmware-shiznats
rm- rf /path/to/vmware-shiznats2
etc
etc
etc
```[/COLOR][/FONT][/SIZE]

---

### Post by aristotlewilde on 2006-10-25
Thanks for the assist.  I did not realize I could do that.  Seems to have worked. It still shows up as a broken package in Synaptic.  When I try to remove, I get this:

> E: vmware-player: subprocess pre-removal script returned error exit status 1

---

### Post by l33tbuntuhax0r on 2006-10-25
c001 g14d 70 h31p

---

### Post by Odisej on 2006-10-31
Can you share the solution as I have a similar problem?

Regards,

Odisej

---

### Post by aristotlewilde on 2006-10-31
My solution was to do a fresh install of Edgy Eft as I had planned on doing so anyway...

The VMWare player in Edgy works really well too.

---

