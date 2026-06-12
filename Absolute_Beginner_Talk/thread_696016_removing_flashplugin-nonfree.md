---
title: "removing flashplugin-nonfree"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by SVWander on 2008-02-13
I am trying to remove flashplugin-nonfree. Actually it was doing an auto update when auto update stopped. There is some problem with flash and I cannot remove it. I tried doing an autoremove and this is the error message I got:

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0 libcrypto++6
The following packages will be REMOVED:
  libcrypto++6 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 18.1kB of archives.
After unpacking 16.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 18.1kB in 0s (26.1kB/s)       
Preconfiguring packages ...
(Reading database ... 92855 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
rm: cannot remove `/var/lib/flashplugin-nonfree/flashplugin-nonfree': Is a directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 88: cho: not found
dpkg: error processing /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Synaptic runs into the same problem. How do I get rid of or reinstall the flash player?
tim

---

### Post by OffAxis on 2008-02-13
have you tried 
```
sudo apt-get autoclean
```

or 
```

sudo apt-get clean
```

?

---

### Post by SVWander on 2008-02-13
> **OffAxis said:**
> have you tried 
```
sudo apt-get autoclean
```

or 
```

sudo apt-get clean
```

?

tried both and it ran the same error message. Then I tried autoremove again and generated this error message:
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0 libcrypto++6
The following packages will be REMOVED:
  libcrypto++6 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 18.1kB of archives.
After unpacking 16.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 18.1kB in 0s (26.1kB/s)       
Preconfiguring packages ...
(Reading database ... 92855 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
rm: cannot remove `/var/lib/flashplugin-nonfree/flashplugin-nonfree': Is a directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 88: cho: not found
dpkg: error processing /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Tim

---

### Post by OffAxis on 2008-02-14
how about 

```
sudo apt-get remove flashplugin-nonfree
```

---

### Post by jan quark on 2008-02-14
```
sudo apt-get remove --purge flashplugin-nonfree 
```

that also deletes the configuration files

---

### Post by SVWander on 2008-02-14
> **OffAxis said:**
> how about 

```
sudo apt-get remove flashplugin-nonfree
```

sudo apt-get remove flashplugin-nonfree
[sudo] password for lap1:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0 libcrypto++6
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 160kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

I then ran the autoremove and got this error message:
 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.8-0 libwxbase2.8-0 libcrypto++6
The following packages will be REMOVED:
  libcrypto++6 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 0 newly installed, 3 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 18.1kB of archives.
After unpacking 16.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 18.1kB in 0s (26.4kB/s)       
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 92860 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
rm: cannot remove `/var/lib/flashplugin-nonfree/flashplugin-nonfree': Is a directory
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 88: cho: not found
dpkg: error processing /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
postinst called with argument `abort-upgrade'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by SVWander on 2008-02-14
> **jan quark said:**
> ```
sudo apt-get remove --purge flashplugin-nonfree 
```

that also deletes the configuration files

I got the same error message as I listed in the post above. The strange thing about it is flash still works! But something is really messed up. I am wondering whether to reinstall. This is a laptop so it is a pain to reinstall the os.

tim

---

### Post by scrumpychap on 2008-02-15
Hi,

I have the same problem. In the middle of auto updating Gutsy, the power went out. After the power cut was fixed, had to do sudo dpkg --configure -a to resurrect the autoupdate feature. Now have exactly the same error regarding flashplugin.

---

### Post by SVWander on 2008-02-15
> **scrumpychap said:**
> Hi,

I have the same problem. In the middle of auto updating Gutsy, the power went out. After the power cut was fixed, had to do sudo dpkg --configure -a to resurrect the autoupdate feature. Now have exactly the same error regarding flashplugin.

I guess that means you haven't found a way around the problem? Actually Flash player still works so I guess that is in my favour but something is broken . . .  plus the update icon is always on showing me the update for flash. I really lost at what to do other than reinstalling.

Tim

---

### Post by scrumpychap on 2008-02-15
You're right, I haven't found a fix. Googling seems to suggest this is a known bug but I haven't seen a fix as yet. Help!

---

### Post by SVWander on 2008-02-16
> **scrumpychap said:**
> You're right, I haven't found a fix. Googling seems to suggest this is a known bug but I haven't seen a fix as yet. Help!

Is you flash working? I know that this isn't elegant but I am to the point where I am going to reinstall the operating system. My documents are all backed up using Simple Backup. I have a source list and everything is backed up to a little server. Of course it seems stupid to fix something that is working. The only thing that isn't working is the flash update. So I have this nice orange cube on my menu bar.

Reinstalling is easy. My a source list . . . somehow (I have never been able to do it) you can use that list to install all the programs you had installed before re installation.

tim.

---

### Post by don2718 on 2008-04-28
> **SVWander said:**
> I am trying to remove flashplugin-nonfree. Actually it was doing an auto update when auto update stopped. There is some problem with flash and I cannot remove it. I tried doing an autoremove and this is the error message I got:

...
rm: cannot remove `/var/lib/flashplugin-nonfree/flashplugin-nonfree': Is a directory
...



I had a similar error, with a slightly different directory name.  From a terminal window, I issued the following command to work around this issue.
```

sudo rm -fr  /var/lib/flashplugin-nonfree/install_flash_player_9_linux

```

---

