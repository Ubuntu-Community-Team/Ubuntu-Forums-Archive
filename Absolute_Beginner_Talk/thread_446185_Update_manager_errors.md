---
title: "Update manager errors"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by fritz_monroe on 2007-05-16
When I brought up my system today, I had updates to install.  I had it install a couple of Samba packages.  I tried to install them but received some errors.  It told me to install from a command line.  So, I did a

 sudo apt-get install -f


This gave me:

```

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2849kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 120408 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.2 (using .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions for how to fix this?

Thanks

---

### Post by shongzah on 2007-05-16
I too had the exact same issue this morning.  Got my groovy little orange star announcing updates, all Samba related.  I went through the usually uneventful process.  At the end it told me that there was an issue and that I should try to fix it with Synaptic or through the commandline.  Neither approach has been very fruitful thus far.

Any help would be greatly appreciated.

---

### Post by shongzah on 2007-05-17
Okay, I may have found an answer.   I went through the steps and would like to know if what I did was a good thing.  [_These folks_]("https://answers.launchpad.net/ubuntu/+question/1556") had the same problem and posted their solution.  Is this a real fix?

Could anyone take a look at that to see if it's okay?

---

