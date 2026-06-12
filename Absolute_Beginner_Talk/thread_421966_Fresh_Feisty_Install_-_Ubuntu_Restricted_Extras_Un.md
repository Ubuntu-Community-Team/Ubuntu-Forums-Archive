---
title: "Fresh Feisty Install - Ubuntu Restricted Extras Unavailable"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-04-24
Hi all, i just installed Feisty on a workstation fresh.  When I try to install Ubuntu Restricted Extras i get an error message about a couple of dependencies not installable.  Everything else seems to be working properly so i don't think it's a cludged install, any ideas?  Thanks in advance for your help.

---

### Post by Happy_Man on 2007-04-24
Did you install ubuntu-desktop? If you don't, then I think that some of the dependencies will not install, because they require a GUI.

---

### Post by BHelts on 2007-04-24
Thanks for the quick reply.  Yes, Ubuntu Desktop is installed.

```

ubuntu-restricted-extras:
 Depends: gstreamer0.10-plugins-ugly but it is not going to be installed
 Depends: sun-java6-plugin but it is not going to be installed

```
This is the exact error i get.

---

### Post by Happy_Man on 2007-04-24
Did you try installing those? From a terminal:

```
sudo apt-get install gstreamer0.10-plugins-ugly sun-java6-plugin
```

---

### Post by BHelts on 2007-04-24
I tried to install those using synaptic, but i did not try with the terminal.  It did not work however, here is the output:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.10-plugins-ugly: Depends: libid3tag0 (>= 0.15.1b) but it is not installable
                              Depends: libmad0 (>= 0.15.1b) but it is not installable
  sun-java6-plugin: Depends: sun-java6-bin (= 6-00-2ubuntu2) but it is not going to be installed
E: Broken packages

```

Thanks for the help!

---

### Post by Happy_Man on 2007-04-24
can you post the output of:

```
cat /etc/apt/sources.list
``` 

please?

---

### Post by BHelts on 2007-04-24
cat /etc/apt/sources.list gives:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main universe restricted multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu feisty-security main universe restricted multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main universe restricted multiverse #Added by software-properties


```

---

### Post by BHelts on 2007-04-24
an interesting update.  when i try to reload sources in synaptic i get this:

```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)


```

must be related?

---

### Post by Happy_Man on 2007-04-24
that could explain it. Perhaps the servers for your area are down. try using the main servers.

---

### Post by BHelts on 2007-04-27
So it's taken a little while for me to get back here, but I am still having the same problem.  I'm sure it is not a repository problem because my laptop is working fine with Feisty.  Any suggestions?

---

### Post by zvacet on 2007-04-27
Do you have all repositories open?Go to the system>administration software properties and chek all boxes there.Reload.
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

---

