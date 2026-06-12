---
title: "Installed (local or obsolete) in Synaptic"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Alveric on 2007-01-03
Just updated from Dapper to Edgy.

I have a list of packages listed in Synaptic as "Installed (Local or Obsolete)"

liblircclient0
linux-image-2.6.15-23-386
linux-image-2.6.15-27-386
linux-restricted-modules-2.6.15-23-386
linux-restricted-modules-2.6.15-27-386

If I try to mark for complete removal - for example liblircclient0 - I get a whole long list of recommended removals which includes rhythmbox, totem, gstreamer and ubuntu-desktop.

What am I supposed to do with these "local or obsolete" packages?

Thanks,

Al.

---

### Post by jblebrun on 2007-01-03
Those are older packages, I believe. Search for linux-image in synaptic, and see if you can force it to install the latest version, which should be 2.6.17. Similar, force it to install the latest version of the other packages. 

This is just a guess, I'm not sure if I'm correct.

---

### Post by Alveric on 2007-01-03
Synaptic says I already have linux-image-2.6.17-10-386 and linux-restricted-modules-2.6.17-10-386

As regards liblircclient, it recommended I install lirc so I did - it hasn't removed it from this Status, though.

Al.

---

### Post by jblebrun on 2007-01-03
So you have 2.6.17, but 2.6.15 are still showing up in the (local or obsolete) section?

---

### Post by jblebrun on 2007-01-03
Are you sure you've updated liblircclient to the latest version? My system has 0.8.0-5ubuntu1.

---

### Post by Alveric on 2007-01-03
As regards the linux-image packages - Yes

As regards liblircclient - 'Properties' gives the package as 0.8.0-9ubuntu1~dapper1

Which is interesting, as I am using Edgy.

Could this be the problem?

Al.

---

### Post by jblebrun on 2007-01-03
Yes, that could be the problem. Select the liblircclient package and hit Ctrl-E. A "force version" dialog should popup. You should be able to select the edgy version from there.

---

### Post by Alveric on 2007-01-03
Thats great!!!  Thanks - it fixed that one.

Any ideas on the old linux-image packages?

Al.

---

### Post by Delkster on 2007-01-03
> **Alveric said:**
> Any ideas on the old linux-image packages?

If you have a newer kernel and it works, you don't need the older versions.

Do you have multiple choices in the boot menu (if any) for the different versions of kernels? If there are and the 2.6.17 option works, you can get rid of the older images.

If you don't have a boot menu or don't know what version of the kernel you're currently running, try entering 'uname -a' on the command line.

Make sure you don't remove your only kernel, though...

---

### Post by Alveric on 2007-01-04
Sorry for long delay - past my bedtime! :) 

If I click to completely remove the old linux-images, I get a whole other list of depending packages which need to be removed and which I'm guessing I don't want to remove...

---

### Post by Delkster on 2007-01-04
> **Alveric said:**
> Sorry for long delay - past my bedtime! :) 

If I click to completely remove the old linux-images, I get a whole other list of depending packages which need to be removed and which I'm guessing I don't want to remove...

What would these be?

The general hierarchy is this:
linux-386 depends on linux-image-386 and linux-restricted-modules-386, thus binding together an 'entire' kernel consisting of the original kernel and a bunch of separate proprietary driver modules

All of these are pseudo-packages only depending on other packages. They don't contain the actual kernel images or driver modules.

linux-image-386 always depends on the latest available linux-image-x.y.z-386 package, where x.y.z is the version. The latest one available for Edgy is linux-image-2.6.17-386.

Likewise, linux-restricted-modules-386, always depends on the latest available restricted-modules package, corresponding to the latest available kernel image. The current actual package for Edgy is linux-restricted-modules-2.6.17-10-386.

Thus, by having linux-386 installed you can guarantee that you have installed everything related to the current kernel. On the other hand, it's not really necessary to have those pseudo packages, it's just nice and useful for keeping up with upgrades and stuff.

The point is that when new kernel versions become available (in dist-upgrades mostly), your system can be made automatically upgrade to the newer kernel even though the package name has changed (since the version number is, unlike in most other Ubuntu/Debian packages, included in the package name) just by providing a new version of the pseudo packages and making the new one depend on the newer actual packages. On the other hand, that's exactly why the older kernels and modules stay around, because they aren't actually upgraded -- instead, a new package with a different name is installed.

If it's just the restricted-modules packages corresponding to the older kernels that are to be removed, you can safely get rid of those as well, but if there's something else that you don't know about, let us know what packages Synaptic wants to remove and we'll see what they're about.

---

