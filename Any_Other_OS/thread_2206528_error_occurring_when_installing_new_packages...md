---
title: "error occurring when installing new packages.."
date: 2014-02-19
forum: Any Other OS
---

### Post by jaison_john on 2014-02-19
whenever I install any new package I receive the following errors:

Setting up se-toolkit (4.2.1-bt0) ...
svn: 'http://svn.trustedsec.com/social_engineering_toolkit' path not found
dpkg: error processing se-toolkit (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up w3af (1.2-bt2) ...
tar: pybloomfiltermmap-0.2.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
/var/lib/dpkg/info/w3af.postinst: line 4: cd: pybloomfiltermmap-0.2.0: No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory
Setting up se-toolkit (4.2.1-bt0) ...
svn: 'http://svn.trustedsec.com/social_engineering_toolkit' path not found
dpkg: error processing se-toolkit (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up w3af (1.2-bt2) ...
tar: pybloomfiltermmap-0.2.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
/var/lib/dpkg/info/w3af.postinst: line 4: cd: pybloomfiltermmap-0.2.0: No such file or directory
python: can't open file 'setup.py': [Errno 2] No such file or directory

have no idea about it...pls help to fix this issue.

---

### Post by ian-weisser on 2014-02-19
You seem to have two problems: se-toolkit and w3af. 

When possible, I recommend using software from the Ubuntu Repositories. That's what this forum supports. While we will try to help you, support for non-Ubuntu packages is provided by whoever put it online.

se-toolkit is not in the Ubuntu Repositories. Where did you get it from?
It's not an easily recoverable error. You should probably whoever you got that package from that it is broken.
Don't try to install it anymore.
Get rid of that broken package with **sudo apt-get clean se-toolkit**
If it keeps trying to install, use **sudo apt-get purge se-toolkit** to stop it.

Your version of w3af is not from the Ubuntu Repositories. Where did you get it from?
You should probably whoever you got that package from that it is broken.
Don't try to install it anymore.
Get rid of that broken package with **sudo apt-get clean w3af**
If it keeps trying to install, use **sudo apt-get purge w3af** to stop it.

---

### Post by jaison_john on 2014-02-20
These packages were installed during an upgrade so it was downloaded by the distribution itself and these errors come every time i manually download any new software....so if I remove these packages will it cause any trouble?
Yes indeed i'm using an ubuntu based distribution hence i felt to post my problem in this forum.

---

### Post by ian-weisser on 2014-02-20
> **jaison_john said:**
> These packages were installed during an upgrade

That seems unlikely. Ubuntu upgrades do not magically add new packages.

Depending upon the distro you are using, it sure seems like you added a PPA, third-party repository, or some .deb from the internet that required those packages. 
We can help you to identify the broken PPA/Repo/deb and remove it. 

Please show us the contents of your /etc/apt/sources.list ( the command is **cat /etc/apt/sources.list** )
Please show us the listing of your /etc/apt/sources.list.d/ directory ( the command is **ls /etc/apt/sources.list.d** )

---

### Post by oldos2er on 2014-02-20
> **jaison_john said:**
> Yes indeed i'm using an ubuntu based distribution hence i felt to post my problem in this forum.

Please clarify which distribution you're running.

---

### Post by jaison_john on 2014-02-22
Backtrack

---

### Post by howefield on 2014-02-22
Thread moved to the "*Other OS/Distro Support*" forum.

---

