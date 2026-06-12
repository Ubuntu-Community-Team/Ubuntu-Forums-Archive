---
title: "[SOLVED] Brother Scan File (Error Removing Repository)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2008-01-20
Hello all,

I installed the brscan2 (Brother Scan Debian Package) for amd64. I was trying to uninstall this package using Synaptic Package Manager, and it returned this error

"E: brscan2: subprocess post-removal script returned error exit status 1"

I've tried restarting, but it is to no avail.

Even more importantly, I cannot install any new packages (I suspect because of this stupid package), The Add/Remove Programs tool will just hang there with a busy cursor. But nothing happens even after 15 minutes.


I don't really care about the brother package, but I need to install new packages! Someone help!

Thanks.

--------------------------------------------
EDIT:

Well I found this [http://ubuntuforums.org/showthread.php?t=425941](http://ubuntuforums.org/showthread.php?t=425941). I did what that guy said, and it still didn't work!

This is my output:

```
root@abhetop:/# mkdir /usr/local/Brother/sane/
mkdir: cannot create directory `/usr/local/Brother/sane/': No such file or directory
root@abhetop:/# mkdir /usr/local/Brother/
root@abhetop:/# mkdir /usr/local/Brother/sane
root@abhetop:/# mkdir /usr/local/Brother/sane/GrayCmData/
root@abhetop:/# mkdir /usr/local/Brother/sane/GrayCmData/ALL
root@abhetop:/# mkdir /usr/local/Brother/sane/GrayCmData/AL
[COLOR="Red"]root@abhetop:/# apt-get remove --purge brscan2[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  krita-data nspluginwrapper libpoppler-qt2 koffice-libs libraptor1
  koffice-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
[COLOR="Red"]1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory[/COLOR]

```

Any ideas?

---

### Post by sirgogo on 2008-01-20
HOLLD ON!

I did it!

I restarted the X-server (I'm not sure how this affects it at all, but anyways) and it worked!


Great success!!:KS

:popcorn:

---

