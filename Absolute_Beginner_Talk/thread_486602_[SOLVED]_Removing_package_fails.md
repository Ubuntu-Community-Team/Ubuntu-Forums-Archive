---
title: "[SOLVED] Removing package fails"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-06-28
Hi I'm trying to remove vmware-player after I'd installed it and it wouldn't play, tried from the launcher and in terminal to see if it gave me an error but there was nothing.

I did sudo apt-get remove and I got an error - told me I had a broken package. 

Tried to remove broken package in synaptic and got 
```

E: vmware-player: subprocess pre-removal script returned error exit status 1
```

tried to purge in terminal and get the same error

```
kevin@kevin-desktop:~$ sudo apt-get --purge remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclan2c2a-sound libclanlib2c2a libtagc0 libssl0.9.7 hermes1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  vmware-player*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129872 files and directories currently installed.)
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

I've looked at similar threads - but having no luck with this.

could someone help me get rid of vmware-player please

---

### Post by forestpixie on 2007-06-28
bump

resolved with a reinstall.

---

### Post by tyfj on 2007-06-28
--:($ sudo   dpkg --remove --force-remove-reinstreq scim-bridge
(Reading database ... 120186 files and directories currently installed.)
Removing scim-bridge ...
Updating the IM modules list for GTK+-2.10.0...Segmentation fault (core dumped)
dpkg: error processing scim-bridge (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 scim-bridge

---

