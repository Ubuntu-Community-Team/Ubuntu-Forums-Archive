---
title: "Hi, need help again pleaseeeee!"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Khurrum on 2007-08-20
Hi, when trying to assign keybindings in metacity I get such errors: 
No database available to save your configuration: Unable to store a value at key '/apps/metacity/global_keybindings/run_command_1', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a lockfile in ~/.gconfd and also lockfiles in individual storage locations such as ~/.gconf


Is there some setting I need to change or maybe do this from root? PLEASE HELP!

---

### Post by jordanmthomas on 2007-08-20
try what it suggests:
log out
press CTRL-ALT-F1
log in there.
type
```
killall gconfd
```
hit enter, 
then, type 
```
rm ~/.gconf*/*lock
```
and then press CTRL-ALT-F7
log back in and see if that helps.


If it still complains, try moving your ~/.gconfd directory elsewhere and let it recreate itself.

---

### Post by hyper_ch on 2007-08-20
And next time use a more descriptive title than "I need help"... just about everyone posting in here needs help.

---

