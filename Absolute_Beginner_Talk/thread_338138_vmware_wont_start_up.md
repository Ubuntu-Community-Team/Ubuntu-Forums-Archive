---
title: "vmware wont start up"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2007-01-14
Hello..
I recently upgraded to edgy and as you would expect, some things don't work anymore. One of them is vmware server. I had a fairly nice little xp drive set up on the guest directory (I used the vmware howto to set it up). Now I click on vmware server and it doen't start up anymore. I can't even get vmware to show a menu or anything. I click it and it tries for a couple of seconds and then it just stares back at me.

Someone know how to fix this?

---

### Post by riven0 on 2007-01-14
Do a reconfiguration:

> sudo /usr/bin/vmware-config.pl

EDIT: BTW, if you have to keep on reconfiguring after every restart [this is the fix for it]("http://www.vmware.com/community/thread.jspa?messageID=65376&#65376").

---

### Post by pebo on 2007-01-21
I've got a similar problem - vmware-server will not start, although it was running w2k fine yesterday. Here's what I get when I start in a terminal: 
```
peter@mesh:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

peter@mesh:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.
```Following riven0's link I created new device nodes with this result: ```
peter@mesh:~$ sudo /etc/init.d/vmware restart
mknod: `/dev/vmnet0': File exists
mknod: `/dev/vmnet8': File exists
mknod: `/dev/vmmon': File exists
mknod: `/dev/vmnet0': File exists
mknod: `/dev/vmnet1': File exists
mknod: `/dev/vmnet2': File exists
mknod: `/dev/vmnet3': File exists
mknod: `/dev/vmnet4': File exists
mknod: `/dev/vmnet5': File exists
mknod: `/dev/vmnet6': File exists
mknod: `/dev/vmnet7': File exists
mknod: `/dev/vmnet8': File exists
mknod: `/dev/vmnet9': File exists
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
peter@mesh:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.
``` so I'm back where I started. 

Help, anyone?

---

### Post by putte30 on 2007-01-23
Same problem here.

---

### Post by tjk on 2007-02-10
> **riven0 said:**
> Do a reconfiguration:

       sudo /usr/bin/vmware-config.pl 


Just wanted to mention that this worked for me.  I couldn't get VMWare to start --- don't know if it was because I installed wine or because I upgraded the kernal.  In any case you may want to try this if you have problems (I used all the defaults for each of the reconfiguration questions).

---

### Post by BOK on 2007-02-12
I'm on kernel 2.6.15-26-686 and tried VMWare Server 1.0.0 and 1.0.1
There seems to be an issue with some libraries:
VMWare needs libhal.so.0 but Ubuntu Edgy has libhal.so.1.0.0 installed. Same for libdbus-glib-1.so.1 --> libdbus-glib-1.so.2.0.0. Symlinking makes no difference, then the hal goes core-dumping...
Any ideas / HOWTOs?

---

### Post by Bachstelze on 2007-02-12
Kernel 2.6.15 = Dapper, not Edgy... Anyway, when exactly do you get the message about the missing libs ?

---

### Post by BOK on 2007-02-12
> **HymnToLife said:**
> Kernel 2.6.15 = Dapper, not Edgy... Anyway, when exactly do you get the message about the missing libs ?

Oh... than apt-get missed something (or I did when upgrading from DD...) OT: any quick way to get this done?
Nevertheless the library-issues would remain, eh?
They appear when starting stuff like "(sudo) vmware" and show up in /tmp/vmware-[root | UID]/*.log

---

### Post by veloce on 2007-02-12
Point 1: vmware server has to recompile some bits and pieces every time you upgrade your kernel.  That's why you need to run vmware-config.pl.

Point 2: The config needs to unload vmware before it can do the recompile.  Going by the error output it is failing to shut down virtual networking.  I'd first try rebooting to see if that allows it to shut down the networking.  If vmware-config.pl still doesn't work, I'd try taking the virtual networks down manually e.g. ifconfig vmnet0 down for each vmnet that is being used.

Good luck.

---

### Post by banditti on 2007-02-12
I had the problem this morning.  I rebooted, which cleared VMware, then ran vmware-config.pl.

All is well now.

---

