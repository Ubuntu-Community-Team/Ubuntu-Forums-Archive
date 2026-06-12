---
title: "vmware server"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by gollybegully on 2007-03-03
Downloaded, setup, installed windows, installed vmware tools everything's running fine.

I restart my computer and today vmware would not start.  I type vmware in a terminal and get 

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


when I run that command I get:

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
Unable to stop services for VMware Server

Execution aborted.





the part that drives me crazy is that everything was running perfect and i didnt change anything all i did was reboot and somehow it magically ****** itself overnight.

---

### Post by ziggykg on 2007-03-05
I'm running VMWare server myself.  I had similar problems when in the beginning I had VMWare Player and tried to uninstall it for the server version.

I suggest uninstalling any vmware apps (server and/or player) and removing any vestiges of vmware (conf files, start-up scripts, etc) and then re-installing vmware server and configuring it.

Also, it may help if you install vmware, not from the repositories but from vmware website.

Hope this helps.

---

