---
title: "[SOLVED] Synaptic Issues ¡HELP!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by hiebert on 2007-09-04
I have a little problem every time I apply the changes made in Synaptic

> E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

I can download everything but when it starts installing I get that screen.. It doesn't happen with every package I choose though.

Could someone please help me?

---

### Post by sbassett on 2007-09-04
Looks like some packages or updates have snuck in that aren't fully satisfied as of yet.

Try the following

```
sudo apt-get -f install
```

---

### Post by hiebert on 2007-09-04
Thank You for your reply

I get the following error message every time i to what you mencioned (have done it several times and i always get this result)

> After unpacking 0B of additional disk space will be used.
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

---

### Post by Happy_Man on 2007-09-04
Try forcing the package to install using the force option in the package menu.

EDIT: Ah, never mind.

---

### Post by hiebert on 2007-09-04
How do i do that? I'm new to this.. :sad:

---

### Post by sbassett on 2007-09-04
Have you tried 

sudo apt-get install cman

?

---

### Post by hiebert on 2007-09-04
same error messages.. It happens with my drivers too.. 

> Errors were encountered while processing:
 clvm
 redhat-cluster-suite
 system-config-cluster
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Happy_Man on 2007-09-04
```
sudo apt-get remove clvm redhat-cluster-suite system-config-cluster
```

On a related note, I've seen this type of error crop up multiple times on the forums lately. What did you install that had these packages as dependencies?

---

### Post by sbassett on 2007-09-04
Then I would execute the following
```
 sudo dpkg -P clvm redhat-cluster-suite system-config-cluster
```

let me know how it turns out.

---

### Post by hiebert on 2007-09-04
Same error code.. ^^v

> Removing system-config-cluster ...
Removing redhat-cluster-suite ...
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)


I just tried to download KMESS for example.. the error message it gave is as following

> E: clvm: subprocess post-installation script returned error exit status 3

---

### Post by hiebert on 2007-09-04
> **sbassett said:**
> Then I would execute the following
```
 sudo dpkg -P clvm redhat-cluster-suite system-config-cluster
```

let me know how it turns out.

> (Reading database ... 123225 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
dpkg - warning: ignoring request to remove redhat-cluster-suite which isn't installed.
Removing system-config-cluster ...
Purging configuration files for system-config-cluster ...
Errors were encountered while processing:
 clvm

Errors again.. Thank you for your replies

---

### Post by hiebert on 2007-09-05
I have tried everything posted earlier.. I even tried the stickies for mi video card drivers and can't get them.. i get to the second part of step 4 and i get following error codes

```
ubuntu1.1_amd64.deb) ...
Unpacking replacement librpcsecgss3 ...
Setting up clvm (2.02.06-2ubuntu9) ...
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error processing clvm (--configure):
 subprocess post-installation script returned error exit status 3
Setting up libkrb53 (1.4.4-5ubuntu3.2) ...

Setting up librpcsecgss3 (0.14-2ubuntu1.1) ...

Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Could someone please help me do this right?

---

### Post by sbassett on 2007-09-05
Looks like clvm is being stubborn. Fire up Synaptic and goto Custom Filters - Broken, and if this package is listed within there, select Edit, Fix Broken Packages. Please let us know.

---

### Post by hiebert on 2007-09-05
This clvm thing is already installed.. I've tried to reinstall it and it gives me this message :confused:

> E: clvm: subprocess post-installation script returned error exit status 3

Am I doing something wrong? Thank you for your replies.. (Again) ;)

---

### Post by sbassett on 2007-09-06
The package is installed, yes, but it looks like it's pretty messed up and preventing further installations. Have you tried the synaptic route mentioned above?

---

### Post by Officer Dibble on 2007-09-06
Is this following a fresh install? It could be that I am very wrong, but when I had serious issues following through on the installation of some basic apps I was shown that it came down to a bad install of Ubuntu.

I was advised to rewrite my CD at a lower speed and install from that.

Once again, I could be wrong in this instance, but it solved my problems. If it is a fresh install you have there, then trying this won't lose you any data, only perhaps a small amount of time.

Your call my friend. :)

---

### Post by hiebert on 2007-09-06
> **Officer Dibble said:**
> Is this following a fresh install? It could be that I am very wrong, but when I had serious issues following through on the installation of some basic apps I was shown that it came down to a bad install of Ubuntu.

I just installed Ubuntu this Monday, so there won't be a big loss of data, I like to try to solve this problem though.. Could you please tell me if the error messages you got were the same?

If my disc had a problem, wouldn't I notice it during the installation? I think that if the disk is damaged, the installation would notice it and won't finish. I really would like to solve this thing, but if it isn't possible, well.. No problem ^^ I`m using Ubuntu for personal research and because I'm sick of Microsoft

> **sbassett said:**
>  Have you tried the synaptic route mentioned above?

Of which Route are you speaking?

---

### Post by hiebert on 2007-09-06
I finally solved the problems with clvm!! I followed some steps at [this]("http://ubuntuforums.org/showthread.php?p=3321772#post3321772") Thread and deleted clvm for now i haven't got any error messages..

Thanks for your help sbassett! I really appreciate it

---

### Post by sbassett on 2007-09-06
Awesome, glad it got taken care of.

---

