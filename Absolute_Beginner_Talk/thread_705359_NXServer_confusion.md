---
title: "NXServer confusion"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by gewitty on 2008-02-23
Can anyone help me out please. I'm trying to set up a remote support service for 2 PC's sitting behind a router/firewall. VNC works OK, but after reading various posts I'm not happy about the level of security or the fact that I have to leave ports open and unsecured.

The threads at [http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976), suggest that NXServer is a far better option. However, the recommendation is to steer clear of the FreeNX packages and instead go for the Desktop edition, which is free to personal users. There are three links listed; one for NX Desktop Server DEB for Linux, another for NX Node DEB for Linux, and a final one for NX Client DEB for Linux. Whilst the link to the client package download works OK, the other two links just drop me straight back to the FreeNX server and node downloads. The only downloads for the Desktop edition of server and node appear to be evaluation packages only.

So, two questions:

1. Does anyone know where the NX Node DEB for Linux and the NX Desktop Server DEB for Linux can be found and
2. Is there an idiots guide to installing/configuring these for simple (secure) remote access purposes.

---

### Post by daflame on 2008-02-26
> **gewitty said:**
> Can anyone help me out please. I'm trying to set up a remote support service for 2 PC's sitting behind a router/firewall. VNC works OK, but after reading various posts I'm not happy about the level of security or the fact that I have to leave ports open and unsecured.

The threads at [http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976), suggest that NXServer is a far better option. However, the recommendation is to steer clear of the FreeNX packages and instead go for the Desktop edition, which is free to personal users. There are three links listed; one for NX Desktop Server DEB for Linux, another for NX Node DEB for Linux, and a final one for NX Client DEB for Linux. Whilst the link to the client package download works OK, the other two links just drop me straight back to the FreeNX server and node downloads. The only downloads for the Desktop edition of server and node appear to be evaluation packages only.

So, two questions:

1. Does anyone know where the NX Node DEB for Linux and the NX Desktop Server DEB for Linux can be found and
2. Is there an idiots guide to installing/configuring these for simple (secure) remote access purposes.

First of all it depends upon whether you have a 32-bit or 64-bit version of Ubuntu.  Depending on which one, you can use NoMachines binaries.  You MUST use all three since they work together.  Their download section should be straight forward.  If you choose NX Free Edition for Linux, then i386 deb or x86_64 deb and download all three and install them.  I have fouind that the only other thing usually needed is nxserver config and adding users.  All the documentation is available on Google and [www.nomachine.com](www.nomachine.com).

This person also has an article:
[http://blog.nikolaidis.com/2007/12/05/installing-nx-free-on-ubuntu-710-gutsy-gibbon/](http://blog.nikolaidis.com/2007/12/05/installing-nx-free-on-ubuntu-710-gutsy-gibbon/)

If you do desire to check out FreeNX after all you can check out my forum here:
[http://ubuntuforums.org/showthread.php?t=620057](http://ubuntuforums.org/showthread.php?t=620057)
There are FreeNX packages for Gutsy in the repos there.

---

