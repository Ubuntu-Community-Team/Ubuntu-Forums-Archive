---
title: "Having Trouble Updating Packages"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by fatsheep on 2007-06-07
I'm running feisty with the envy script and ever since I upgraded I have not been able to update three pacakges: nvidia-glx, nvidia-glx-dev, and [ia32-libs]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fi%2Fia32-libs-gtk%2Fia32-libs-gtk_25_amd64.deb&md5sum=e810a79e9dece355c4737998732b2de1&arch=amd64&type=main").   Any help on a remedy would be greatly appreciated, below is the output of **sudo apt-get upgrade**.  

> **fatsheep:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  nvidia-glx nvidia-glx-dev
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/17.9MB of archives.
After unpacking 5460kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 166907 files and directories currently installed.)
Preparing to replace ia32-libs 1.5ubuntu5 (using .../ia32-libs_1.5ubuntu9_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libaudio.so.2.4', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by fatsheep on 2007-06-07
Bump

---

### Post by NeoLithium on 2007-06-07
Try
```

sudo aptitude -f upgrade

```

---

### Post by fatsheep on 2007-06-08
> **NeoLithium said:**
> Try
```

sudo aptitude -f upgrade

```

The results are identical to those of sudo apt-get upgrade:

> 
**fatsheep:~$ sudo aptitude -f upgrade**
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  nvidia-glx nvidia-glx-dev 
The following packages will be upgraded:
  ia32-libs 
1 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/17.9MB of archives. After unpacking 5460kB will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 160292 files and directories currently installed.)
Preparing to replace ia32-libs 1.5ubuntu5 (using .../ia32-libs_1.5ubuntu9_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libaudio.so.2.4', which is also in package ia32-libs-openoffice.org
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by fatsheep on 2007-06-09
Any ideas?

---

### Post by fatsheep on 2007-06-17
Reported a conflict with ia32-libs and  ia32-libs-openoffice.org on launchpad: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/119611](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/119611).  After cleaning up previous nvidia graphic card installation with envy and reinstalling the nvidia driver, nvidia-glx and nvidia-glx-dev were removed with no side effects.

---

