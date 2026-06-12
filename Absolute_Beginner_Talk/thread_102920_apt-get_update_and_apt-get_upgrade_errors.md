---
title: "apt-get update and apt-get upgrade errors"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by frootstripe on 2005-12-13
uname -a:

Linux homeytop 2.6.12-10-k7 #1 Fri Nov 18 12:46:18 UTC 2005 i686 GNU/Linux

***********
After running update and upgrade with apt-get, I get the following msg. what does it mean?

Running newaliases
 * Starting Postfix Mail Transport Agent...
postfix/postfix-script: fatal: the Postfix mail system is already running
   ...fail!
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postfix

---

### Post by sonny on 2005-12-13
Starting Postfix Mail Transport Agent...
postfix/postfix-script: fatal: the Postfix mail system is already running
...fail!
invoke-rc.d: initscript postfix, action "start" failed.

It is trying to start Postfix, wich you have running, so it can not start it because it is already "started", perhaps you should kill the process before doing what you were doing. In a console type "sudo killall postfix" or search in /etc/init.d for that process and then type "sudo /etc/init./postfix stop" or something close to the name of the process.

---

### Post by frootstripe on 2005-12-13
thanx for your response.

I'm wondering, do I really even need postfix? I'm just using web-based email.

---

### Post by sonny on 2005-12-13
well in case you would have kmail or thunderbird to mange your accounts. It's pretty nice to have your mail in your pc, helps you save space in your web account, unless you have gmail... hehehehehehe...

---

### Post by kori.mendocino on 2005-12-13
For most of the home users, postfix is rather useless.

---

### Post by frootstripe on 2005-12-13
"apt-get remove postfix" prompts to remove the following packages:

lsb lsb-core lsb-cxx lsb-graphics mailx mutt postfix

Don't really know much about lsb, is it safe to remove all of these?

---

