---
title: "Something wrong with my package manager."
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-09-12
I recently installed Gutsy Daily-Build (Sep 11 build) and am getting the following errors whenever I try to install / upgrade, but not removing.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu9) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
update-alternatives: unable to make /usr/lib/midbrowser/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/midbrowser-flashplugin: No such file or directory
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

Has anyone else been getting this problem?

---

### Post by splintercellguy on 2007-09-12
Try removing flashplugin-nonfree and reinstalling?

---

### Post by chris062689 on 2007-09-12
Nope.
I'm going to downgrade back to 7.04.
7.10 is coming along VERY nicely though, can't wait for the final release!

---

