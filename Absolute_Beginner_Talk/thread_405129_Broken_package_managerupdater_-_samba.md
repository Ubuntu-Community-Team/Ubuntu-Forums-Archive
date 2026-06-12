---
title: "Broken package manager/updater - samba?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Fraoch on 2007-04-09
Yesterday was the first time I used my Ubuntu 6.06 installation since September, so there were 172 updates.

They downloaded properly and started to install OK, but when it got to one of the "i386" files it suddenly returned an error about MySQL.  This could have been because of [SlimServer]("http://www.slimdevices.com/su_downloads.html").

Now I am left with a broken package, 60 uninstalled updates and an updater that keeps instructing me to fix broken packages in Synaptic Package Manager.

I checked [http://ubuntuforums.org/showthread.php?t=404876](http://ubuntuforums.org/showthread.php?t=404876) and tried all the fixes there but keep getting:

```
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/2845kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 102334 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any help?  I've stopped SlimServer so MySQL should be available to be stopped, but that doesn;t seem to be the problem now.

Thanks!

---

### Post by Fraoch on 2007-04-09
I tried uninstalling samba through Synaptic Package Manager, but that won't complete either, I get the same

```
subprocess new pre-removal script returned error exit status 102
```

error as I get when I try to repair or install.

So still stuck!  Any help?  Please?

---

### Post by Fraoch on 2007-04-09
Success!

After some more searching, I tried:

[http://ubuntuforums.org/archive/index.php/t-6318.html](http://ubuntuforums.org/archive/index.php/t-6318.html)

which worked!

I'll see what happens when I try to reinstall samba, but for now things are OK!

---

