---
title: "How do I reconfigure my Add/Remove"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by cjssmo on 2007-06-05
How do I reconfigure my application management system.  I get this error when I go to Applications-->Add/Remove

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I have not modified my sources.list in any way

This is the output when I run "sudo apt-get install -f

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ampache-3.3.3.2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7557kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133361 files and directories currently installed.)
Removing ampache-3.3.3.2 ...
dpkg: error processing ampache-3.3.3.2 (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 ampache-3.3.3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

Actually this box is being used as a test computer, a friend of mine is packaging Ampache for ubuntu and he asked me to test his first initial packaging attempts.  If I could reconfigure the package management system it would save me a lot of time.  Yes I understand the importance of using a fresh install, but until the package build quites borking the system I would like to just reconfigures (if possible).

Thank you

---

### Post by ramjet_1953 on 2007-06-05
There a few processes that can fix broken package problems.

Lets try the easy way first.

Navigate to [COLOR="Blue"]System>Administration>Synaptic Package Manager[/COLOR]

Enter your password, when prompted

When Synaptic opens, click [COLOR="Blue"]Edit>Fix Broken Packages[/COLOR]

Click on the [COLOR="Blue"]Reload button[/COLOR]

If this doesn't fix it, we will then need to use some command line stuff.

Regards,
Roger :cool:

---

### Post by cjssmo on 2007-06-05
Didn't work.

---

