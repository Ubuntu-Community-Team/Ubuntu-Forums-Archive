---
title: "error while upgrading 7.04 to 7.10-rc"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Bruno Amaral on 2007-10-13
When I ran the command update-manager -d the program showed some error messages.

After it was finally finished, I found out I can't access the internet.
So I tried dpgk-reconfigure -a rebooted and still nothing. 

I tried to re-install the broken packages with apt-get install -f :
```

.bruno@wednesday:~$ sudo apt-get install -f
[sudo] password for bruno:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up dhcp3-client (3.0.5-3ubuntu4) ...
chown: cannot access `/lib/dhcp3-client/call-dhclient-script': No such file or directory
dpkg: error processing dhcp3-client (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on dhcp3-client; however:
  Package dhcp3-client is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dhcdbd:
 dhcdbd depends on dhcp3-client; however:
  Package dhcp3-client is not configured yet.
dpkg: error processing dhcdbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on dhcdbd (>= 1.12-2); however:
  Package dhcdbd is not configured yet.
dpkg: error processing network-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on network-manager (>= 0.6.5); however:
  Package network-manager is not configured yet.
dpkg: error processing network-manager-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dhcp3-client
 ubuntu-minimal
 dhcdbd
 network-manager
 network-manager-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

I don't know what to do next. Can anyone point me in the right direction ?

---

### Post by louieb on 2007-10-13
Gutsy has its own section if you look there you would find you need to run sudo dhclient to get an internet connection. That is if your using broadband. Its a bug.

---

### Post by Bruno Amaral on 2007-10-13
From what I could gather, dhclient isn't even properly installed. 

I run dhclient3 and get a segmentation fault (core dumped) error

---

### Post by dr_wily on 2007-10-26
Hello, 

I get the same error when i use the following commands: dpkg --configure -a and apt-get install -f. Here is what I get:

Setting up acpid (1.0.4-5ubuntu8) ...
 * Loading ACPI modules...                                               [ OK ] 
 * Starting ACPI services...                                                    invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-desktop:
 kubuntu-desktop depends on acpi-support; however:
  Package acpi-support is not configured yet.
 kubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
 kubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing kubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
 kubuntu-desktop


I've read your comments and Im not having any problems with dhclient or dhclient3. Hence I was wondering how I could fix the problem so I can finish installing my packages. 

Thank you,

Eric

---

