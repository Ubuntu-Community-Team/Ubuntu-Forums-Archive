---
title: "Dependency Problems - Leaving Unconfigured"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by gdoermann on 2007-06-01
When I try to install certain programs (or it may be all programs) I get this error:

An Error Occurred
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

This is the log:

(Reading database ... 149011 files and directories currently installed.)
Removing acidrip ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d : initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of redhat-cluster-suite:
 redhat-cluster-suite depends on clvm; however:
  Package clvm is not configured yet.
dpkg: error processing redhat-cluster-suite (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-cluster:
 system-config-cluster depends on redhat-cluster-suite; however:
  Package redhat-cluster-suite is not configured yet.
dpkg: error processing system-config-cluster (--configure):
 dependency problems - leaving unconfigured

---

### Post by gdoermann on 2007-06-01
The programs install, but they don't always work correctly.

This was a log from the uninstall, but I get the same errors when installing.

---

### Post by gdoermann on 2007-06-02
I thought the topic fit better under installation and setup:
[http://ubuntuforums.org/showthread.php?t=461648]("http://ubuntuforums.org/showthread.php?t=461648")
Anyhow, I found the solution.

---

### Post by gdoermann on 2007-06-02
This has been a wonderful conversation... with myself...

---

### Post by reddroad on 2007-06-06
Hi Friend,
  I am sorry to see that you didn't get any responses to your post. I am a new and very green user,
so that is a little discouraging. I noticed in your post that you found the solution to this problem, and as I am having exactly the same problem, would you mind sharing. Any help you could give me would be appreciated.

---

### Post by gdoermann on 2007-06-07
> **reddroad said:**
> Hi Friend,
  I am sorry to see that you didn't get any responses to your post. I am a new and very green user,
so that is a little discouraging. I noticed in your post that you found the solution to this problem, and as I am having exactly the same problem, would you mind sharing. Any help you could give me would be appreciated.

Reddroad,
Yea, it wasn't too bad though.  I figured it out by putting many different articles about clvm together.  The bug was reported on the Ubuntu bug website, but without any resolutions.  This is what I did and it worked:

What you need to do is uninstall and reinstall clvm.  Clvm is a cluster management program (See [this page]("http://packages.ubuntu.com/feisty/admin/clvm") for more information on clvm).  

So first to uninstall clvm. The problem is the bug keeps you from uninstalling or reinstalling clvm. So you need to do a few things manually.  Since that last post was your first I am assuming you are very new to Ubuntu (I'm sorry if I'm insultingly simplifying).

First, backup your current clvm file (in the terminal- Applications-> Accessories->Terminal ):

```
sudo cp /etc/init.d/clvm /etc/init.d/clvm_backup
```

Type in the root password and it will backup the file.

Then download the attached file and go to the directory where it is in the terminal (cd [dirctory])
unzip it, then copy it to the folder as the new clvm

```
tar -xvzf clvm.tar.gz
sudo cp clvm_new /etc/init.d/clvm
```

Now uninstall this version

```
sudo apt-get remove clvm
```

Then reinstall the latest version from the server:

Code:
```

sudo apt-get install clvm

```
Volia! Your bug is fixed!

Let me know if you have any problems.

---

### Post by reddroad on 2007-06-07
Howdy friend,
  Thanks for the reply! I have been trying to follow the threads and to accomplish what you have described here but I am afraid I am just too green with Linux. I have backed up the old clvm file and downloaded the attachment to the desktop. I have even extracted it to the desktop. That is where I am stuck. I guess I am not keen enough to open the right directory as when I enter the code as in this thread I get no such file or directory, or something to that effect. Any suggestions, and please remember that I am as green as a gourd when it comes to working with linux.

---

### Post by terabite on 2007-06-13
did u try manual reconfigure?

```
sudo dpkg --configure clmv
```

it works sometimes...

---

### Post by reddroad on 2007-06-25
Thanks for the reply Terrabite. I found a post in another section of the forum that was very simple and cleared it up right away. I have since forgotten what I did, sorry. One of my Hard drives crashed the other day so I have been offline with this box for a whlie.

---

### Post by m_atif on 2007-06-27
That really works! Thanks gdoermann
I wonder why such dependency problems come along so often.

---

