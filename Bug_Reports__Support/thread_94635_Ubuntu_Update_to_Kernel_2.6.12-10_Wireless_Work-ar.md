---
title: "Ubuntu Update to Kernel 2.6.12-10 Wireless Work-around"
date: 2005-11-24
forum: Bug Reports / Support
---

### Post by newbie2 on 2005-11-24
[http://lxer.com/module/newswire/view/48365/](http://lxer.com/module/newswire/view/48365/)

---

### Post by jdong on 2005-11-24
(1) This has nothing to do with Backports.. The Ubuntu Security Team released the update to correct numerous security issues with the kernel. People were properly warned in the security update: [http://ubuntuforums.org/showthread.php?p=511314#post511314](http://ubuntuforums.org/showthread.php?p=511314#post511314)

> 

ATTENTION: Due to an unavoidable ABI change this kernel has been given
a new version number, which requires you to recompile and reinstall
all third party kernel modules you might have installed. If you use
linux-restricted-modules, you have to update that package as well to
get modules which work with the new kernel version. Unless you
manually uninstalled the standard kernel metapackages (linux-386,
linux-powerpc, linux-amd64-generic), a standard system upgrade will
automatically perform this as well.


(2) The article makes the thing sound like rocket science. What happened was a simple ABI change, which means all kernel modules need to be recompiled. If you're using 100% Ubuntu stuff, everything has already been recompiled for you. If you have your own modules you manually installed, then you'll need to recompile them (typically by going through the install procedure again). The article LXer decided to publish just beats around the bush and doesn't show any effort to get users to understand what happened, nor does it try to explain that wireless is NOT the only thing affected. At times I doubt the author's Linux expertise, because it seems like he's assuming everyone compiles their own NDiswrapper which is not true -- Ubuntu's included ndiswrapper works quite  well most of the times.

---

