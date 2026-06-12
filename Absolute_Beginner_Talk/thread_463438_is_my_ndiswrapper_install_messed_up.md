---
title: "is my ndiswrapper install messed up?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-06-03
```

gail@badassness:~$ sudo aptitude install ndiswrapper-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  ndiswrapper-common 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.7kB of archives. After unpacking 81.9kB will be used.
Writing extended state information... Done
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 116657 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.18-1ubuntu2_all.deb) ...
Setting up ndiswrapper-common (1.18-1ubuntu2) ...
gail@badassness:~$ sudo aptitude install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "ndiswrapper-utils-1.9"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
gail@badassness:~$ sudo aptitude install ndiswrapper-utils-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  ndiswrapper-utils-1.8 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/29.0kB of archives. After unpacking 131kB will be used.
Writing extended state information... Done
Selecting previously deselected package ndiswrapper-utils-1.8.
(Reading database ... 116667 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.8 (from .../ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils-1.8 (1.18-1ubuntu2) ...
gail@badassness:~$ ndiswrapper
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
gail@badassness:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.22
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
gail@badassness:~$ 

```

i'm having trouble installing my windows wireless drivers so i uninstalled the ndiswrapper from synaptic & tried again thru terminal & it still gives an error when i do ndiswrapper -v

do i have to compile it to get it working on this computer?

---

### Post by patsfan on 2007-06-03
try fwcutter

---

### Post by lunaz on 2007-06-03
more info re: fwcutter?
looked at desc in synaptic & i don't understand what it will do for me.

---

