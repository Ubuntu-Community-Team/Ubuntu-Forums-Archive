---
title: "Moblock issues"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2008-01-22
Hey there im getting this issue when trying to install:

Reading database ... 87713 files and directories currently installed.)
Removing moblock-nfq ...
Stopping MoBlock   ...done.
Purging configuration files for moblock-nfq ...
dpkg run finished!
Selecting previously deselected package moblock.
(Reading database ... 87684 files and directories currently installed.)
Unpacking moblock (from .../moblock_0.9~rc1-6+gutsy_i386.deb) ...
Setting up moblock (0.9~rc1-6+gutsy) ...
Reloading MoBlock failed. Trying an update instead, this may take several minutes.
You may do in another terminal a "tail -f /var/log/moblock-control.log"
to follow the update process. Pressing "control" + "c" stops this.
The lists are saved to /var/spool/moblock/.
Updating blocklists and reloading MoBlock failed.
No blocklist in /etc/moblock/ipfilter.dat.
Try a "moblock-control update" to complete the installation.
dpkg: error processing moblock (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
Moblock

How do i get around this?

Using Kubuntu 7.1 and adept

adpet says this at %80 of install:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

---

### Post by wolfen69 on 2008-01-22
i cant really help you with moblock, but if you use ktorrent or azureus, you can import blocklists. [http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4](http://www.bluetack.co.uk/forums/index.php?act=dscriptca&CODE=viewcat&cat_id=4) you will probably want level1 list if you use p2p. make sure blocklist is unzipped first if you go with ktorrent.

---

### Post by dynamethod on 2008-01-22
Sweet tyvm!, i use Ktorrent, its strange though cause everytime i try load the bluetack pages, well.. it doesnt load lol, connection times out :S

---

### Post by jre on 2008-01-22
As it stated in the messages:
```
Try a "moblock-control update" to complete the installation.
```

greets
jre

---

