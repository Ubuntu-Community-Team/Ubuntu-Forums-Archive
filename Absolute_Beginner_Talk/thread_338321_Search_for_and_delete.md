---
title: "Search for and delete"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by chris90uk on 2007-01-14
Hello

I am trying to remove everything to do with VMware from my computer because it has not uninstalled properly from Automatix so it won't install again. I have managed to search the filesystem but I can't delete what I find, even when searching from a root Nautilus window. The permissions are read and write. Can someone help me to delete anything with VMware in the filename?

Thanks.

---

### Post by taurus on 2007-01-14
Applications -> Accessories -> Terminal
```
sudo rm **filename**
-or-
sudo rm -rf **directory**
```

---

### Post by chris90uk on 2007-01-14
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo rm **filename**
-or-
sudo rm -rf **directory**
```

Thanks for that, but I have tried both of those swapping the bold words for '*vmware*' and it has only removed one thing, there are 79 items left to do with VMware.

---

### Post by taurus on 2007-01-14
What directory is VMWare installed to?

---

### Post by chris90uk on 2007-01-14
> **taurus said:**
> What directory is VMWare installed to?

How do I find that out please?

---

### Post by taurus on 2007-01-14
```
sudo find / -name vmware* -print
```

---

### Post by chris90uk on 2007-01-14
> **taurus said:**
> ```
sudo find / -name vmware* -print
```

/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.postinst
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.list
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.postrm
/var/lib/dpkg/info/vmware-player-kernel-modules-2.6.17-10.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules.md5sums
/var/lib/dpkg/info/vmware-player-kernel-modules.list
/var/lib/dpkg/info/vmwareworkstation.list
/var/lib/dpkg/info/vmware-player.list
/var/lib/dpkg/info/vmwareworkstation.shlibs
/var/lib/dpkg/info/vmwareworkstation.postinst
/var/lib/dpkg/info/vmware-player.postrm
/var/lib/dpkg/info/vmwareworkstation.postrm
/var/lib/dpkg/info/vmwareworkstation.prerm
/var/lib/dpkg/info/vmwareworkstation.conffiles
/var/lib/dpkg/info/vmwareworkstation.md5sums
/var/lib/dpkg/info/vmwareworkstation.preinst
/var/cache/apt/archives/vmware-player_1.0.2-2_i386.deb
/var/cache/apt/archives/vmware-player-kernel-modules_2.6.17.10_i386.deb
/var/cache/apt/archives/vmware-player-kernel-modules-2.6.17-10_2.6.17.7-10.1_i386.deb
/etc/init.d/vmware
/etc/init.d/vmware-player
/etc/vmware
/lib/modules/2.6.17-10-generic/vmware-player
/lib/modules/2.6.17-10-386/vmware-player
/usr/share/doc/vmware-player-kernel-modules-2.6.17-10
/usr/share/doc/vmware-player-kernel-modules
/usr/share/doc/vmware
/usr/share/doc/vmwareworkstation
/usr/share/man/man1/vmware.1.gz
/usr/share/man/man4/vmware.4.gz
/usr/share/app-install/desktop/vmware-player.desktop
/usr/share/app-install/icons/vmware-player.png
/usr/bin/vmware-config.pl
/usr/bin/vmware
/usr/bin/vmware-mount.pl
/usr/bin/vmware-loop
/usr/bin/vmware-vdiskmanager
/usr/bin/vmware-ping
/usr/lib/xorg/modules/drivers/vmware_drv.so
/usr/lib/vmware-player
/usr/lib/vmware-player/bin-debug/vmware-vmx
/usr/lib/vmware-player/bin/vmware-vmx
/usr/lib/vmware
/usr/lib/vmware/bin-debug/vmware-vmx
/usr/lib/vmware/bin/vmware
/usr/lib/vmware/bin/vmware-vmx
/usr/lib/vmware/messages/ja/vmware.vmsg
/usr/lib/vmware/share/icons/48x48/apps/vmware-workstation.png
/usr/lib/vmware/share/icons/48x48/apps/vmware-player.png
/usr/lib/vmware/share/pixmaps/vmware-player.png
/home/chris/Desktop/OS/vmware.log
/home/chris/Desktop/OS/vmware-0.log
/home/chris/Desktop/OS/vmware-1.log
/home/chris/Desktop/OS/vmware-2.log

That's what it showed.

---

### Post by taurus on 2007-01-14
Since you used automatix2 to install it, why don't you use it to uninstall it?

---

### Post by chris90uk on 2007-01-14
> **taurus said:**
> Since you used automatix2 to install it, why don't you use it to uninstall it?

That's what I used, but it's left some on my computer, and now it won't install, reinstall, uninstall or anything.

---

### Post by arnieboy on 2007-01-15
Automatix installs Vmware-Player in Ubuntu Multiverse which is a broken package and they have done nothing in 4 months to fix it.
This is a case of a broken post installation file. Try the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postinst
sudo apt-get remove vmware-player
```
and check to see if the error appears again.
If its **not fixed**, try the following:```

sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo apt-get remove vmware-player
```

---

