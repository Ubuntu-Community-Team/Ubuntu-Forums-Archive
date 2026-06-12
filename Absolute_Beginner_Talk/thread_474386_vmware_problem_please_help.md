---
title: "vmware problem please help"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by sirab on 2007-06-15
I get this error while trying to install the modules in terminal
> 
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.3-1) ...
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
/etc/init.d/vmware-server: 766: /usr/lib/vmware-player/net-services.sh: not found
invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
sirab@sirab-laptop:~$ 

help thanks =]

---

### Post by gcos7 on 2007-06-15
Perhaps this link can help (it has a link for changes you must make if you are running 7.04:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

---

