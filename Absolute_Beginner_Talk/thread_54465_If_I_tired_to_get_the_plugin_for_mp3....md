---
title: "If I tired to get the plugin for mp3..."
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Muhammad on 2005-08-04
...and I got all this:

```
muhammad@ubuntu:~$ sudo apt-get update
Err http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com hoary-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Ign http://archive.ubuntu.com hoary Release
Err http://us.archive.ubuntu.com hoary-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://security.ubuntu.com hoary-security Release
Ign http://archive.ubuntu.com hoary/multiverse Packages
Ign http://us.archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://archive.ubuntu.com hoary/multiverse Sources
Ign http://us.archive.ubuntu.com hoary-updates Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://security.ubuntu.com hoary-security/restricted Packages
Err http://archive.ubuntu.com hoary/multiverse Packages
  Temporary failure resolving 'archive.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Err http://archive.ubuntu.com hoary/multiverse Sources
  Temporary failure resolving 'archive.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://security.ubuntu.com hoary-security/restricted Sources
Ign http://us.archive.ubuntu.com hoary/main Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://security.ubuntu.com hoary-security/universe Packages
Ign http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://security.ubuntu.com hoary-security/universe Sources
Ign http://us.archive.ubuntu.com hoary/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Err http://security.ubuntu.com hoary-security/main Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary/universe Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Err http://security.ubuntu.com hoary-security/restricted Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary-updates/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Err http://security.ubuntu.com hoary-security/main Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary-updates/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://security.ubuntu.com hoary-security/restricted Sources
  Temporary failure resolving 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary-updates/main Sources
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://security.ubuntu.com hoary-security/universe Packages
  Temporary failure resolving 'security.ubuntu.com'
Ign http://us.archive.ubuntu.com hoary-updates/restricted Sources
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://security.ubuntu.com hoary-security/universe Sources
  Temporary failure resolving 'security.ubuntu.com'
Err http://us.archive.ubuntu.com hoary/main Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/restricted Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/main Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/restricted Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/universe Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/universe Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/main Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/restricted Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/main Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/restricted Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
muhammad@ubuntu:~$ sudo apt-get install totem-xine w32codecs libdvdcss2 gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package totem-xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package totem-xine has no installation candidate
muhammad@ubuntu:~$

```

What does it mean?

---

### Post by Ampersand on 2005-08-04
is this the same computer you used to post this? If so, try again. If not, check your network settings, then try again.

---

### Post by Muhammad on 2005-08-04
It is the same computer... Do I have to fix my proxy settings? and if so.. How?

---

### Post by Muhammad on 2005-08-04
Also I'm getting an error while trying to update Firefox... Do you think maybe I should have sticked with Windows because all of the questions I asked today are annoying? :(

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Muhammad]Also I'm getting an error while trying to update Firefox... Do you think maybe I should have sticked with Windows because all of the questions I asked today are annoying? :([/QUOTE]

No. You are not being annoying. I was working on something:

[http://www.ubuntuforums.org/showthread.php?p=287220#post287220](http://www.ubuntuforums.org/showthread.php?p=287220#post287220)

First things first: Are you connected to the internet? if so, use synaptic:

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

Soo....the problem with Firefox is that you have to have it closed to update it.

For mp3s, that is SO easy to fix.

I like the program Xmms. Like Winamp it is. To install search for 

"xmms-mad" and "xmms" and install both.

Then use this command:

> killall gnome-panel

It should be in your Applications menu then.

Don't give up, I'll help.

---

### Post by spahn on 2006-07-21
I think that i am having the same problems (it is a bigger issue than not being able to get the mp3 plugin), i think it is an internet connection issue- maybe something is not allowing the computer to connect to the internet on certain sources.

[http://ubuntuforums.org/showthread.php?t=220493](http://ubuntuforums.org/showthread.php?t=220493)

i tried installing xmms mad and got this:
```

$ sudo apt-get install xmms-mad
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xmms-mad: Depends: libglib1.2 (>= 1.2.0) but it is not installable
            Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
            Depends: libid3tag0 (>= 0.15.0b) but it is not installable
            Depends: libmad0 (>= 0.15.1b) but it is not installable
            Depends: xmms but it is not installable
            Depends: xmms but it is not installable
E: Broken packages

```
I have been dealing with this issue for almost two weeks, and people in the office already make fun of me for using Linux... this is just going to give them more confidence in Windows! I have to fix this issue!!!
Any help would be greatly appreciated.

---

