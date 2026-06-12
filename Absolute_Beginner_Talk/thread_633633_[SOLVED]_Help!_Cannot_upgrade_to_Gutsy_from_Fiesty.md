---
title: "[SOLVED] Help! Cannot upgrade to Gutsy from Fiesty!!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by lamalex on 2007-12-06
Hey all, I'm having problems using the network upgrade to get from fiesty to gutsy. I believe the problem is something with dbus, when I run the update-manager from the command line it exits with this error
```
warning: could not initiate dbus
extracting '/tmp/tmpl84c-M/gutsy.tar.gz'
authenticate '/tmp/tmpl84c-M/gutsy.tar.gz' against '/tmp/tmpl84c-M/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 914, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 178, in run
    self.runDistUpgrader()
  File "/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py", line 53, in runDistUpgrader
    if os.getuid() != 0:
NameError: global name 'os' is not defined

```
dbus is currently running according to ps. Is there another way to do this? I'd rather not need to download the alt install cd and do it that way.


[EDIT] [http://ubuntuforums.org/showpost.php?p=3577769&postcount=4](http://ubuntuforums.org/showpost.php?p=3577769&postcount=4)

A friend of mine found it, thanks everyone anyway.

---

