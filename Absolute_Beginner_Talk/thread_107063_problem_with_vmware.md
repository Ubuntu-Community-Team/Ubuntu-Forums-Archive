---
title: "problem with vmware"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by o_owd on 2005-12-22
hello,
i installed vmware 5.5.1 like shown here ([https://wiki.ubuntu.com/InstallingVMWare?action=show&redirect=VmWare+guide%3A+How+to+install+VMware+in+Breezy)](https://wiki.ubuntu.com/InstallingVMWare?action=show&redirect=VmWare+guide%3A+How+to+install+VMware+in+Breezy)).

in the guide sais
"Users running VMware 5.5.0 build 18463 (or above) should not use the 'vmware-any-any-update' package as this will cause the following sorts of errors: Version mismatch with vmmon module: expecting 137.0, got 116.0. Try reinstalling VMware Workstation. To fix this problem, run the version of vmware-config.pl included in the VMware package. If have already run the version in the vmware-any-any-update package, rerun the vmware-install.pl script to reinstall VMware. "

i already did that and i stiil get the error. in fact there are three :

"version mismatch with vmmon module: expecting 137.0 got 122.0. you have an incorrect version of 'vmmon' kernel module. try reinstalling vmware"
"failed to initialize monitor device"
"unable to change virtual machine power state: cannot find a valid peer process to connect to"

any help with this ? please ?

thanks.

---

### Post by gnu2tux on 2005-12-22
I cannot vouch for the wiki page that you gave's accuracy, however I have vmware 5.5 working great on breezy.

I simply downloaded the .tar.gz from their website and installed it that way.

I ran vmware-config.pl when prompted and it told me that vmware was incompatible with my current kernel. This isn't a problem as long as you have gcc and the kernel downloaded:

```

$sudo apt-get install gcc kernel-headers-x

```

where kernel headers matches your kernel version:

```

$uname -a
Linux foo 2.6.10-6-386 #1 Fri Nov 18 11:53:02 UTC 2005 i686 GNU/Linux

```

therefore I downloaded the kernel-headers-2.6.10-6-386 package, which installs to /usr/src/2.6.10-6.386/

simply tell vmware-config where to find the headers it needs and it'll compile a suitable module for your kernel with gcc.

after all that, vmware ran sweet just by typing vmware at the prompt.

Let me know how you get on.

Cheers!

---

### Post by o_owd on 2005-12-23
i uninstalled it and install it again and it works. thanks for helping.

---

### Post by woland on 2005-12-26
I have linux kernel headers installed where you specified (2.6.12.10-k7) but I could specify this location.
I have another copy of headers at /lib/modules/2.6.12-10-k7/build/include, what the vmware installer proposes but I keep getting the same error message o_owd was getting. Where am I wrong?

Thanks in advance!

Update:

Solved it by reinstalling vmware, but without the use of vmware-any-any-update96

---

