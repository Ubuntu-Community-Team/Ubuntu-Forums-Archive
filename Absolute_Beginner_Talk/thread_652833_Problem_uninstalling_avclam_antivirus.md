---
title: "Problem uninstalling avclam antivirus"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by necrocago on 2007-12-29
[SIZE="2"][B]Weeks ago, I installed Avclam antivirus. As I didn't find it useful for me I uninstalled it with add/remove applications manager and then I cleaned some relative avclam files using synaptic package manager.
The problem is that I checked on the running services and I found that there is still a service called avclam antivirus daemon. how could I remove completely and purgue the avclam antivirus instalation.
Any help?.
Thanks[/B][/SIZE]

---

### Post by daengbo on 2007-12-29
Avclam or clamav? I'll assume you meant the latter, but if I'm wrong, please tell me.

Open Synaptic and do a name search for clamav. Make sure all the clamav* and libclamav* (especially clamav-daemon) packages are marked for complete removal. Click apply. That should stop the daemon.

You can check by hitting ALT-F2 and typing the following
gksudo gnome-system-monitor

This will open the system monitor as root (in administrator mode). In the Processes tab, look for a clamav daemon. There shouldn't be one, but if there is, you can end the process by clicking on the End Process button.

It will be completely removed.

That's it.

---

### Post by tgilber1 on 2007-12-29
You could try the following:

1.  sudo dpkg -l "*clam*"
2.  Verify that you do not see any clam packages installed

_Example output_
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  clamav         0.91.2-3ubuntu antivirus scanner for Unix
ii  clamav-base    0.91.2-3ubuntu base package for clamav, an anti-virus utili
ii  clamav-daemon  0.91.2-3ubuntu antivirus scanner daemon
pn  clamav-data    <none>         (no description available)
rc  clamav-docs    0.91.2-3ubuntu documentation package for clamav, an anti-vi
ii  clamav-freshcl 0.91.2-3ubuntu downloads clamav virus databases from the In
un  libclamav      <none>         (no description available)
ii  libclamav1     0.88.4-1ubuntu virus scanner library
ii  libclamav2     0.91.2-3ubuntu virus scanner library


ii = installed
un = never installed
rc = removed, but config files exist
pn = purged - package and config files

To purge a package using apt-get, package must be installed
1.  reinstall package and purge it
2.  sudo apt-get purge clamav

To purge a package after it has been uninstalled - use dpkg
1.  sudo dpkg --purge clamav

---

### Post by necrocago on 2007-12-31
**:)** Thanks you so much guys for your help!!!. 
It worked!!!
Have you guys a happy 2008!!!
THANKS

---

