---
title: "&quot;No installation candidate&quot;"
date: 2012-09-14
forum: Any Other OS
---

### Post by ChinaJustin on 2012-09-14
OK, so I'm trying to install  lirc on my computer to get the little infrared remote that came with my  old HP laptop working. Using Mint 13 32-bit with (yeah, it's not Ubuntu, but it's based on Ubuntu 12.04, and I see that this error isn't necessarily tied to any one version of Ubuntu).

When I do a "sudo apt-get install lirc" I get this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lirc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lirc-x

E: Package 'lirc' has no installation candidate
```Great, I thought, so I'll try lirc-x.

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
 lirc-x : Depends: lirc (= 0.9.0-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```Wait, broken packages? So, I tried sudo apt-get install -f:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```The three that aren't upgraded are the linux kernal updates. My questions:

1) What's going on?
2)  I can download the .tar at the lirc website, but I'm afraid of  dependency issues, considering the above errors. Would this be a viable  option?
3) Why is it telling me that lirc (and, below, g++ and dpkg-dev) is uninstallable?

My sources.list is the following:

```
deb http://mirror.cse.ucdavis.edu/linuxmint.com/packages maya main upstream import
deb-src http://mirror.cse.ucdavis.edu/linuxmint.com/packages maya main upstream import
deb http://mirror.anl.gov/pub/ubuntu/ precise main restricted universe multiverse
deb http://mirror.anl.gov/pub/ubuntu/ precise-updates main restricted universe multiverse
deb http://mirror.anl.gov/pub/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
```Help? I've tried "sudo apt-get clean" and "sudo apt-get autoclean" followed by an update/upgrade, all to no avail.

I also tried installing build-essential through apt-get, and get the same kind of "not installable" error:

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
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not installable
                   Depends: dpkg-dev (>= 1.13.5) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Perfect Storm on 2012-09-14
Moved to Other OS/Distro Talk.

---

