---
title: "Installing Video Driver ATI"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Torn on 2007-01-02
trying to update my video with a HOWTO and came into this error, and im unsure what to do next.

ll
outlaw@outlaw-desktop:~/Desktop/ATI$bash ./ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg ubuntu/edgy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.32.5........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./ati-driver-installer-8.32.5-x86.x86_64.run: ./ati-installer.sh: /bin/sh: **bad interpreter: No such file or directory**
Removing temporary directory: fglrx-install
outlaw@outlaw-desktop:~/Desktop/ATI$

The HOWTO im reading can befound [>Here<]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by spockrock on 2007-01-02
may I suggest the much easier repository method

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

---

### Post by Torn on 2007-01-02
Its the same HOWTO!

just.. down a bit further ><;

Lets have them jump through the hoops, then tell them theres an easier way

---

### Post by Torn on 2007-01-02
Few commands down i ran into this error

The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.6MB of archives.
After unpacking, 30.2MB of additional disk space will be used.
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true
outlaw@outlaw-desktop:~/Desktop/ATI$

---

### Post by Torn on 2007-01-02
so i tried  sudo aptitude install xorg-driver-fglrx-dev
having more luck installing options with the -dev behind it

i recieved a slighty diffrent yet similar effect
The following NEW packages will be automatically installed:
  xorg-driver-fglrx
The following NEW packages will be installed:
  xorg-driver-fglrx xorg-driver-fglrx-dev
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 111kB/10.7MB of archives. After unpacking 30.7MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted xorg-driver-fglrx-dev 7.0.0-8.25.18+2.6.15.12-1 [111kB]
Fetched 111kB in 2s (51.1kB/s)
[B]E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true[/B]
A package failed to install.  Trying to recover:
outlaw@outlaw-desktop:~/Desktop/ATI$

trying to google the error to find something on it

---

### Post by mcrae on 2007-01-02
> **Torn said:**
> trying to u....
.......................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
./ati-driver-installer-8.32.5-x86.x86_64.run: ./ati-installer.sh: /bin/sh: **bad interpreter: No such file or directory**
....
The HOWTO im reading can befound [>Here<]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I thing this has something to do with your shell, or morew precisely that you are missing the right shell. Cheq in synaptic what do you have
I'm not 100% sure but I have had similar problem

---

### Post by Torn on 2007-01-02
What sort of things would i be looking for in synaptic?

---

### Post by Torn on 2007-01-02
Looked up fglrx, and checked it for install, currently undergoing see how it turns out when it finishes

---

### Post by Torn on 2007-01-02
Its just hanging... im going to restart

---

### Post by Torn on 2007-01-02
Well had to hard reboot it and was welcomed to 


INIT:Cannot Execute "/etc/init.d/rcs
Entering Runlevel 2
INIT:Cannot Execute "/etc/init.d/rc

/bin/sh: bad interpreter: No such file or directory
/bin/sh: bad interpreter: No such file or directory
root@none#

so im suspecting this is where i reinstall
having only 3 days into this im not surprized
figured eventually i was going to screw this over bad enough

now if i can manage to re-install correctly

---

### Post by Torn on 2007-01-02
yay reinstalled -_-l

and updated my card 1st thing!

---

