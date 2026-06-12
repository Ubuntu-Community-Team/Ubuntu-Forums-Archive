---
title: "Can't uninstall vmware"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by tylerjroach on 2007-07-05
I tried to get vmware to work and it didn't work with my kernel version and I also accidentally deleted the /etc/vmware file and now i get this error```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 127822 files and directories currently installed.)
Removing vmware-player ...
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
/etc/init.d/vmware-player: 175: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
If anyone knows how i can uninstall vmware or recover the /etc/vmware file to uninstall it that way please help. Thank you.

---

### Post by bulldog060 on 2007-07-05
this is more for it not working with your kernel version: what message did it give you? I ran into problems with my install but that was because it wanted the header files for the kernel I was running ( which you can get through synaptic ).

you might want to try grabbing the headers, forcing the install to make it replace what is currently on the system and see if everything starts up. After you do the forced install if you still can't get it working or don't want to play around with it at least you will be able to do a clean uninstall.

~ron

---

### Post by tylerjroach on 2007-07-05
It could not set up my monitor or network card with my kernel and i gave up and i am now reinstalling it and trying to get the right kernel set up with it and hopefully that will work

---

