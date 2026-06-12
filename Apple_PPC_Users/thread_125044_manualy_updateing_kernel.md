---
title: "manualy updateing kernel???"
date: 2006-02-02
forum: Apple PPC Users
---

### Post by penguain on 2006-02-02
the latest kernel for PPC is 2.6.12-10
i've downloaded 2.6.16.2 from ppckernel.org
```
tar xjf linux-*.tar.bz2
cd linux-*
cp boot/vmlinux-* /boot
cp boot/System.map-* /boot
cp -R lib/modules/* /lib/modules
```

and then 
If you are using yaboot, you will need to add this kernel to your configuration and re-run ybin -v.

will that work with Kubuntu 5.10???

Thanks

---

### Post by towsonu2003 on 2006-02-02
check out this: [http://ubuntuforums.org/showthread.php?t=85064](http://ubuntuforums.org/showthread.php?t=85064)
I'm not sure whether the procedure is the same for all archs.

---

