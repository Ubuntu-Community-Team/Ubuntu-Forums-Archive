---
title: "broken package in adept"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Chamith on 2007-02-15
Hi,

I have been getting the following error in Adept when I try to install any package

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

When I go in through aptitude it says that the package is extremeley inconsistant and that I should manually fix it.

The problem started when I was installing <<sun-java5-bin>> via Adept and my computer shutdown mid-install.

thanks,

---

### Post by mssever on 2007-02-15
Try purging sun-java5-bin and see if that clears the matter up.

---

### Post by PPAAUULL on 2007-02-15
Just wondering but why did your computer shutdown mid-install? Power outage?

---

### Post by Chamith on 2007-02-16
hey,

I tried purging via aptitude but it didn't work.

The installation was interupted since the Java installer asks for confirmation input on the software policy and I wasn't able to enter data into the installer through adept.  (i.e. it was asking me for input but adept did not allow me to enter any input)... so i cancelled.  pretty silly of me eh?

---

### Post by Chamith on 2007-02-16
under aptitude..the options for <purge> or <remove> gives me a warning to reinstall the package since its 'extremely inconsistant'

the error for <reinstall> is as follows

<<E: I wasn't able to locate a file for the sun-java5-bin package. This might mean you need to manually fix this package. (due to missing arch)>>

---

### Post by Chamith on 2007-02-16
I used dpkg to force a purge and it seemed to have gotten everything in order.

Thanks,

FYI

<<sudo dpkg --force-remove-reinstreq --purge sun-java5-bin>>

---

### Post by nawhki on 2007-06-04
I have the same problem with a broken package clvm and tried your solution on the konsole and some thing like written at the bottom came out... I can still install the packages in adept, but always at the end of the installation adept crashed ,though the package is normally properly installed 

nawhki@nawhki-laptop:~$ sudo dpkg --force-remove-reinstreq --purge clvm
(Reading database ... 141392 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm

any ideas ?

---

