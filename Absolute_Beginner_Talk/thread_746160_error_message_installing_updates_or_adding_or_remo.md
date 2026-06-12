---
title: "error message installing updates or adding or removing packages"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by klick.here on 2008-04-05
every time install a package or remove one or update i get this afterwards:    E: emifreq-applet: subprocess post-installation script returned error exit status 2.   it doesn't seem to be hurting anything but I was wondering why and I just don't like error messages on my desktop:???:

---

### Post by Michael.Godawski on 2008-04-05
Nobody likes error messages.
What happens if you run these terminal commands?

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by klick.here on 2008-04-06
first this : 
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet
then this :
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  torcs-data-tracks torcs-data-cars
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

