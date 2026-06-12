---
title: "Cannot remove package"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by erkgeek on 2006-09-20
Hello everyone.

Recently, I installed rageircd through synaptic and now I cannot remove it. Here are the errors I get trying to remove it..

(Reading database ... 98142 files and directories currently installed.)
Removing rageircd ...
ERR: Not starting Rage IRC Daemon: Conffile /etc/rageircd/rageircd.conf missing
invoke-rc.d: initscript rageircd, action "stop" failed.
dpkg: error processing rageircd (--purge):
 subprocess pre-removal script returned error exit status 1
ERR: Not starting Rage IRC Daemon: Conffile /etc/rageircd/rageircd.conf missing
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

I don't understand why it is trying to start at first? Any help would be appreciated.

---

### Post by tommcd on 2006-09-20
Did the program work ok before you tried to remove it? Just guessing, but it seems from the error message that it faile to install completely. You could try 'mark for reinstallation' in synaptic, then after it reinstalls just remove via synaptic.
This should not harm anything anyway. If this did not work, then: 'sudo apt-get remove rageircd.
Hope this helps.

---

### Post by erkgeek on 2006-09-20
Hi, thanks for the reply. Well actually, you guessed right. I had a problem when trying to install and so I tried removing to discover this problem. I can try reinstalling it but I get the following error when I do.

Setting up rageircd (2.0.1-5) ...
Adding system user
adduser: Warning: The home dir you specified already exists.
Allowing use of questionable username.
The user `Debian-rageircd' already exists as a system user. Exiting...
ERR: Not starting Rage IRC Daemon: Conffile /etc/rageircd/rageircd.conf missing
invoke-rc.d: initscript rageircd, action "start" failed.
dpkg: error processing rageircd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 rageircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

