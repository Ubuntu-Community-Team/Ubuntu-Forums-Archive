---
title: "[SOLVED] dpkg no longer works"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by amazingtaters on 2008-03-04
So, I installed VMware Server, and then decided to leave it, as I needed some sleep. Well, now whenever I try to use Synaptic or Update Manager, I get this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I decided to delete /etc/vmware, since apparently vmware is the root of my problem. Before doing this, running "dpkg --configure -a" started to do what it was supposed to, then was hijacked by VMware. Now, I get this output-

```
 sudo dpkg --configure -a
Setting up vmware-server (1.0.4-1gutsy2) ...
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server

```

If I try "sudo apt-get install dpkg" this happens:

```
 sudo apt-get install dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dpkg is already the newest version.
The following packages were automatically installed and are no longer required:
  libpigment0.3-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.4-1gutsy2) ...
cp: cannot create regular file `/etc/vmware/locations': No such file or directory
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So, what can I do to fix this problem?

---

### Post by Sef on 2008-03-04
Did you run ```
sudo dpkg --configure -a
```?

---

### Post by hyperair on 2008-03-04
Try:
```
sudo mkdir /etc/vmware
```

Then run:
```
sudo dpkg --configure -a
``` again

---

### Post by amazingtaters on 2008-03-04
hokay, so scratch this, I found a workaround with some google-foo that fixed it. Thanks for the quick replies though.

---

### Post by kesman on 2008-03-04
you should install vmware again with apt-get install --reinstall vmware or whatever the packagename was that you installed vmware with. Then uninstall it. Never manually remove any directory that is created with an installer.

---

