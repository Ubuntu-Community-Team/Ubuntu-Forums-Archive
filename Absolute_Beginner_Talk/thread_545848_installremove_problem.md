---
title: "install/remove problem"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by macruadhi on 2007-09-08
Whenever I try to install a new package, I apply the changes, the packages download, then I get the error message:

E: xfonts-intl-european: subprocess post-removal script returned error exit status 2


I've uninstalling that font package, but it won't go away.

Thanks,
Eric

---

### Post by forestpixie on 2007-09-08
try to purge it

```
 sudo apt-get remove --purge xfonts-intl-european
```

---

### Post by macruadhi on 2007-09-08
Does this mean it worked or not?


eric@eric-laptop:~$  sudo apt-get remove --purge xfonts-intl-european
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xfonts-intl-european
0 upgraded, 0 newly installed, 1 to remove and 122 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 315kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157576 files and directories currently installed.)
Removing xfonts-intl-european ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exitdpkg: error processing xfonts-intl-european (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xfonts-intl-european
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by forestpixie on 2007-09-08
no it doesn't - try

```
sudo apt-get install -f
```

if that doesn't either

```
sudo dpkg -C
```

When you installed the xfonts-intl-european did you get an error?

---

### Post by macruadhi on 2007-09-08
Well, I tried:

eric@eric-laptop:~$ sudo dpkg -C
Password:
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 xfonts-intl-european International fonts for X -- European


Then I tried to reinstall, no luck, then I tried a complete uninstall:

E: xfonts-intl-european: Package is in a very bad inconsistent state - you should


I am very stumped.

---

