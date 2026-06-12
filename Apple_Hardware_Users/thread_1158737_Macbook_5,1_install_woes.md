---
title: "Macbook 5,1 install woes"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by Ru5tyNZ on 2009-05-14
Hey everyone,

I just installed jaunty and am trying to get everything working on my Macbook 5,1 (mainly the sensors and fans).

I new so I've been following this guide: [https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)

But when it comes to installing the applesmc-dkms pack I get this (are things not configured and installed correctly?):

```

james@james-laptop:~$ sudo apt-get install applesmc-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
applesmc-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up usbhid-dkms (0.11.2) ...
Loading new usbhid-0.11.2 DKMS files...

Error! Cannot locate /usr/src/usbhid-0.11.2.dkms.tar.gz.
File does not exist.
dpkg: error processing usbhid-dkms (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bcm5974-dkms:
 bcm5974-dkms depends on usbhid-dkms; however:
  Package usbhid-dkms is not configured yet.
dpkg: error processing bcm5974-dkms (--configure):
 dependency problems - leaving unconfigured
Setting up hid-dkms (0.11.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Loading new hid-0.11.1 DKMS files...

Error! Cannot locate /usr/src/hid-0.11.1.dkms.tar.gz.
File does not exist.
dpkg: error processing hid-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 usbhid-dkms
 bcm5974-dkms
 hid-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Your help would be greatly appreciated.

---

### Post by Ru5tyNZ on 2009-05-14
Is there an easy way to delete and purge the package? So I can reinstall.

---

### Post by gotgenes on 2009-05-14
Looks like you have some packages that didn't install fully. Try running
```
sudo apt-get install --fix-broken
```

---

### Post by cyberdork33 on 2009-05-14
and you shouldn't need that package anymore in Jaunty

---

### Post by Ru5tyNZ on 2009-05-14
> **cyberdork33 said:**
> and you shouldn't need that package anymore in Jaunty


Thank you for your responses. I uninstalled the packages in the guide and then reinstalled them. Seems to be correctly installed this time.

@cyberdork

Really? I was just following the guide. Should I uninstall them?

The only problem I'm having now is with the trackpad; I can't right click. I'm sure I'v followed the instructions down to the letter(blacklisting usbhid, etc). Is there some sort of debug information I could provide so someone can help me solve this?

Thanks again,
James

---

### Post by cyberdork33 on 2009-05-16
yep the applesmc module that is part of the jaunty kernel is just fine.

you don't have to uninstall it, but you don't need it either.

Here is a bug on the touchpad thing:
[https://bugs.edge.launchpad.net/mactel-support/+bug/337935](https://bugs.edge.launchpad.net/mactel-support/+bug/337935)

---

