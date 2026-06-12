---
title: "Unmet dependencies in open office updates"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by baja munda on 2007-10-06
Platform: Kubuntu Feisty.

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-style-default: Depends: openoffice.org-style-andromeda (= 2.2.0-1ubuntu5) but 2.2.0-1ubuntu4 is installed
E: Unmet dependencies. Try using -f.

---

### Post by por100pre1 on 2007-10-06
Try This:

```
sudo apt-get install -f
```

---

### Post by mail480697 on 2007-10-09
Fails for me:

$sudo apt-get -s upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  python-uno: Depends: openoffice.org-core (= 2.0.4-0ubuntu6) but 2.0.4-0ubuntu7 is installed
E: Unmet dependencies. Try using -f.

$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  python-uno
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/225kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 163517 files and directories currently installed.)
Preparing to replace python-uno 2.0.4-0ubuntu6 (using .../python-uno_2.0.4-0ubuntu7_amd64.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 935, in run
    pkg.remove(runtimes, remove_script_files=True)
  File "/usr/bin/pycentral", line 693, in remove
    default_runtime.remove_byte_code(self.private_files)
AttributeError: 'NoneType' object has no attribute 'remove_byte_code'
dpkg: error processing /var/cache/apt/archives/python-uno_2.0.4-0ubuntu7_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-uno_2.0.4-0ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

---

### Post by zvacet on 2007-10-09
[http://packages.ubuntu.com/feisty/editors/openoffice.org-style-andromeda]("http://packages.ubuntu.com/feisty/editors/openoffice.org-style-andromeda")

See if you have installed package marke with red ball.If not install it first,and after that install your dependency.

---

### Post by mail480697 on 2007-10-09
It's installed already

dpkg -s  openoffice.org-common
Package: openoffice.org-common
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 34932
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: openoffice.org
Version: 2.2.0-1ubuntu5

---

