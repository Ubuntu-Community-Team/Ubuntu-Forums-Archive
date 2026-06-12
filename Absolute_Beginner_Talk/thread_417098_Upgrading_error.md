---
title: "Upgrading error"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by JimmyLightning on 2007-04-21
Hey, the other day I was trying to upgrade from Dapper to Edgy and I got the following error:

> Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6.2_i386.deb) ...
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package xli
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've tried going and removing all the files from /usr/X11R6/bin (which is what the first version of this error told me to do, I got that error while trying a GUI upgrade, this error is what came when I was trying a command-line upgrade) but I still get the error. 

Any ideas?

Thanks!

-jimmy

---

### Post by JimmyLightning on 2007-04-21
Maybe I should give more details:

I tried to do the "GUI upgrade" by doing command " update-manager -c " and then clicking on "upgrade to Ubuntu 6.10", all went well, until I got an error that said it couldn't delete the files in /usr/X11R6/bin, so I went and deleted said files and then tired again, then it started giving me other errors which I'm pretty sure were simaliar to the above one. Then I tried to do a command line upgrade and got that error (I believe the command was sudo apt-get dist-upgrade when I got that above quoted error). 

I'm wondering if the problem is that I wasn't logged in as root, do I need to be logged in as root to upgrade? If so, how do I log in as root? I tried using username "root" and the password I type in when I'm opening things like the update manager, but that didn't work.

Any ideas would be helpful.

Thanks!

~j

---

### Post by webramp on 2007-05-29
Try dpkg -r xli

---

