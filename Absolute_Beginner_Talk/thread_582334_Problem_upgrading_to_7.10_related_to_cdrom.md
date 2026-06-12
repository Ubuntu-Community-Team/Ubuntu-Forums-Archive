---
title: "Problem upgrading to 7.10 related to cdrom"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by SuperCool4678 on 2007-10-19
I got this error message when I tried to upgrade to Gutsy.  Can anyone tell me what I need to do?

Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/dists/feisty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

---

### Post by linuxwizard on 2007-10-19
Try removing or disable extra repos you added to your source list. Than try to install again.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by JBAlaska on 2007-10-19
You also need to disable your cdrom source in **System, Administration, Software Sources, Third-Party Software tab, uncheck "CD Rom Ubuntu 7.04 feisty fawn"** 

On a side note after you upgrade, The Medibuntu Gutsy repo is now up.

Ubuntu 7.10 "Gutsy Gibbon":
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

GPG Key:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by SuperCool4678 on 2007-10-21
[QUOTE=JBAlaska;3576278]You also need to disable your cdrom source in **System, Administration, Software Sources, Third-Party Software tab, uncheck "CD Rom Ubuntu 7.04 feisty fawn"** 

How do you get there?  I can't find anything like that.

---

### Post by rsambuca on 2007-10-21
> **SuperCool4678 said:**
> [QUOTE=JBAlaska;3576278]You also need to disable your cdrom source in **System, Administration, Software Sources, Third-Party Software tab, uncheck "CD Rom Ubuntu 7.04 feisty fawn"** 

How do you get there?  I can't find anything like that.

You can get there from your top menu bar.  Click "System -> Administration -> Software Sources"...

---

### Post by SuperCool4678 on 2007-10-23
> **rsambuca said:**
> [QUOTE=SuperCool4678;3593177]

You can get there from your top menu bar.  Click "System -> Administration -> Software Sources"...

I don't have anything called "Administration" under my "System" tab, and I don't even have a "top menu bar."  I'm using KDE, not GNOME.

---

### Post by rsambuca on 2007-10-23
Sorry, I don't know the kde equivalent.  You can change it manually though```
kdesu kate /etc/apt/sources.list
```

---

