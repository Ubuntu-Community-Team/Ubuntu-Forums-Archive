---
title: "how to uninstall koffice 1.6 (manually)"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by secret_force on 2006-09-10
I installed koffice 1.6 (alpha1) a few weeks ago. With Koffice beta1 out, I wanted to install this version however I first need to deinstall alpha1. The problem is, I can't find the directory where Koffice is installed. Does anyone know :confused:?? I just did a default install so i'm looking for the default directory.

---

### Post by whizbaby on 2006-09-10
**sudo updatedb**    (...takes a little)
**locate koffice|less**

This would show you the occurances of *kubuntu* in your filesystem and give them as an argument to **less** so that it is displayed a little nicer (quit with q-key).

---

### Post by secret_force on 2006-09-10
This is the result after i did the steps you mentioned. I don't know what to do with these results. Can anyone see in which directory koffice 1.6 is  installed

> 
/var/lib/dpkg/info/koffice-data.list
/var/lib/dpkg/info/koffice-data.md5sums
/var/lib/dpkg/info/koffice-data.postinst
/var/lib/dpkg/info/koffice-data.postrm
/var/lib/dpkg/info/koffice-libs.list
/var/lib/dpkg/info/koffice-libs.md5sums
/var/lib/dpkg/info/koffice-libs.postinst
/var/lib/dpkg/info/koffice-libs.postrm
/var/lib/dpkg/info/koffice-libs.shlibs
/home/ernst/.kde/share/config/kofficerc
/home/ernst/.kde/share/apps/RecentDocuments/koffice-1.5.90.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-data.postrm.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-data.list.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-libs.list.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-libs.shlibs.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-data.postinst.desktop
/home/ernst/.kde/share/apps/RecentDocuments/koffice-data.md5sums.desktop
/home/ernst/.kde/share/apps/koffice
/home/ernst/.kde/share/apps/konversation/logs/freenode_#koffice.log
/usr/include/kofficeversion.h
/usr/include/koffice_export.h
/usr/lib/kde3/kfile_koffice.la
/usr/lib/kde3/kfile_koffice.so
/usr/lib/kde3/kofficescan.la
/usr/lib/kde3/kofficescan.so
/usr/lib/kde3/kofficethumbnail.la
/usr/lib/kde3/kofficethumbnail.so
/usr/lib/libkofficecore.so.3
/usr/lib/libkofficecore.so.3.0.0
/usr/lib/libkofficeui.so.3
/usr/lib/libkofficeui.so.3.0.0
/usr/lib/libkofficecore.so
/usr/lib/libkofficecore.la
/usr/lib/libkofficeui.so
/usr/lib/libkofficeui.la
/usr/share/apps/koffice
/usr/share/apps/koffice/autocorrect
/usr/share/apps/koffice/autocorrect/autocorrect.xml
/usr/share/apps/koffice/autocorrect/en_US.xml
/usr/share/apps/koffice/hyphdicts
/usr/share/apps/koffice/hyphdicts/dicts.xml


BTW do I really need to deinstall koffice 1.6alpha before installing koffice 1.6 beta. Or will the beta simply overwrite the alpha code.

---

### Post by whizbaby on 2006-09-10
This seems to be a normal install, so you can remove the installation by typing (in terminal)
**sudo apt-get remove koffice**
(or
**dpkg -r koffice**)

---

