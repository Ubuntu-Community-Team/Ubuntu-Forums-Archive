---
title: "Gnome problem returns - anything to do with looking for non-existent network?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Tzumli_D on 2006-12-11
My previous problem with the gui taking a long time to open up after logging on has reoccurred after I turned the computer off, and turned it on again.

To fix it I was guided to do:
 *sudo apt-get install --reinstall gnome-control-center-dev*
And my results were:
[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-control-center-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.6kB of archives.
After unpacking 143kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main gnome-control-center-dev 1:2.16.1-0ubuntu4 [75.6kB]
Fetched 75.6kB in 3s (22.1kB/s)                  
Selecting previously deselected package gnome-control-center-dev.
(Reading database ... 122360 files and directories currently installed.)
Unpacking gnome-control-center-dev (from .../gnome-control-center-dev_1%3a2.16.1-0ubuntu4_all.deb) ...
Setting up gnome-control-center-dev (2.16.1-0ubuntu4) ...
[/I]
I relaunched it a couple of times after doing this (that is restart rather than turning off) and the gui came up almost immediately.
From reading other threads I am wondering if this has anything do with an icon on the desktop saying "no network connection".
At the end of my login I get the following message:

[I]"There was an error starting the GNOME Settings Daemon.
Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in."
[/I]
The computer is a stand alone PC with a broadband connection which is working just fine.

Denise

---

### Post by auburn on 2006-12-14
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)

network-manger was causing my problem.

---

