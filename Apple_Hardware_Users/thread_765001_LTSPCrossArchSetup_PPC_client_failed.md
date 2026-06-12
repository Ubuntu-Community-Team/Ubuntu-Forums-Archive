---
title: "LTSPCrossArchSetup PPC client failed"
date: 2008-04-24
forum: Apple Hardware Users
---

### Post by vfxjbg on 2008-04-24
Hi,

I have followed the instructions here : [https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup](https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup)
But I'm not able to complete the building of the ltsp for Powerpc. (testing on powermac G4)

Somebody has an idea why the chroot failed ?

Thanks in advance

```
 sudo ltsp-build-client
NOTE: adding default dist and components to security mirror:
http://security.ubuntu.com//ubuntu hardy main restricted
I: Retrieving Release
I: Retrieving Packages
I: Retrieving Packages
I: Retrieving Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
W: Failure trying to run: chroot /opt/ltsp/powerpc mount -t proc proc /proc
error: LTSP client installation ended abnormally

```

---

### Post by dogma106 on 2008-06-11
I have this exact same problem, does anyone have any suggestions. vfxjbg: Did you ever find a solution?

---

### Post by loomerds on 2008-09-09
I'm also getting this problem.  Has anyone figured out a work-around?

---

### Post by enochbrown on 2010-07-29
If anyone has a working PPC chroot, could they tar it and share it. K12Linux has done this, so it is easy to setup... but I would prefer to be able to use Ubuntu.

---

### Post by LinuxJediMaster on 2011-02-15
It seems the PowerPC client option failed a while ago and no one has come up with a fix. I am hoping to understand LTSP and perhaps create my own image by hand. If I do, I will post the URL to the 'root' image and show how I did it.

---

