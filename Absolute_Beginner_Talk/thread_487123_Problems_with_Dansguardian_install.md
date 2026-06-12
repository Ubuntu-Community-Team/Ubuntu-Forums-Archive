---
title: "Problems with Dansguardian install"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by merlin114 on 2007-06-28
Hi, I've just switched to Dapper from WinXP and have been trying to get Dansguardian working for days. I've read zillions of how-to's and I've installed DG 2.8.0.6, TinyProxy 1.6.3.3, and firehol 1.231-4 per the instructions from one of the threads. I also edited dansguardian.conf and tinyproxy.conf as instructed. After reboot, I have no indication that dg is working at all, and I'm not getting any content filtering in Firefox or Epiphany. I found one other thread that suggested typing "sudo dpkg-reconfigure dansguardian", so I did that and got the following error:

Stopping DansGuardian: dansguardian.
Starting DansGuardian: Error reading file:
Error reading file:
Error opening exceptionvirussitelist
Error opening filter list:/etc/dansguardian/dansguardianf1.conf
Error reading filter group conf file(s).
Error parsing the dansguardian.conf file or other DansGuardian configuration fil es
/etc/init.d/dansguardian: line 33: 7304 Segmentation fault start-stop-daem on --start --quiet --pidfile /var/run/$NAME.pid --exec $DAEMON
invoke-rc.d: initscript dansguardian, action "start" failed.

I'm new to Linux and don't understand most of the instructions I'm trying to follow. I've also looked for the dansguardian_install_gui which is mentioned in the threads and is supposed to make this easier, but all I find at the christianubuntu link is the gui for Feisty -- it seems like they removed the downloads for dapper and edgy. I'm beginning to think it would be easier to just install ubuntuCE-Feisty, but it took me so long to get things set up to see my other hard drive (NTFS) and get some 3rd party commercial software installed, I'm afraid to start over with a new load. Can anyone help me get DG working on Dapper? Please?!

---

