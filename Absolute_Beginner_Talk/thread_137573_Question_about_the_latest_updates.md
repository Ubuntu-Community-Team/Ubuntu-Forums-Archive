---
title: "Question about the latest updates?"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-02-28
Hi everyone,
Below are, what seems to be to me, kde-related updates. I got this list by  clicking on "Update Manager":
> kcontrol/kdebase-bin/kdebase-data /kdelibs-bin/kdelibs-data/kdelibs4c2/kicker/libconq4/

I still have lots to learn but one thing I know is that I use Gnome and not KDE.

Why do I get KDE-related updates? Do I need to download/install them because somehow they are needed by my system? If someone can throw a light on this, I'd be most grateful.

---

### Post by localzuk on 2006-02-28
Have you at anytime used kde on your machine? Can you select as your session type when you log in?

---

### Post by Perfect Storm on 2006-02-28
Perhaps you have some KDE related applications which need those libs and now the updater found that there's some updates for it now.

---

### Post by xyz on 2006-02-28
I cannot select kde as a session type when I log in.
I don't know if this helps but I typed:
```
locate kde
```
and I got this:
> warning: locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/etc/kde3
/etc/kde3/colors
/etc/kde3/colors/Royal
/etc/kde3/colors/Web
/etc/kde3/colors/40 Colors
/usr/share/man/man8/blockdev.8.gz
/usr/share/applications/synaptic-kde.desktop
/usr/share/applications/smeg-kde.desktop
/usr/share/icons/gnome/48x48/filesystems/gnome-fs-blockdev.png
/usr/share/icons/Human/scalable/filesystems/gnome-fs-blockdev.svg
/usr/share/mime/inode/blockdevice.xml
/usr/share/gnome-app-install/icons/atlantikdesigner.xpm
/usr/share/gnome-app-install/icons/kdeprintfax-16.xpm
/usr/share/gnome-app-install/icons/kdeprintfax.xpm
/usr/share/gnome-app-install/atlantikdesigner.desktop
/usr/share/gnome-app-install/kcmkded.desktop
/usr/share/gnome-app-install/kdepasswd.desktop
/usr/share/gnome-app-install/kdeprintfax.desktop
/usr/share/gnome-app-install/kdevassistant.desktop
/usr/share/gnome-app-install/kdevdesigner.desktop
/usr/share/gnome-app-install/kdevelop3.desktop
/usr/share/gnome-app-install/synaptic-kde.desktop
/usr/include/linux/kdev_t.h
/usr/include/asm/kdebug.h
/usr/include/asm-i386/kdebug.h
/usr/include/asm-x86_64/kdebug.h
/home/th/.kde
/home/th/.kde/share
/home/th/.kde/share/applnk
/home/th/.kde/share/applnk/klik
/home/th/.kde/share/applnk/klik/.directory
/home/th/.kde/share/applnk/klik/klik.desktop
/home/th/.kde/share/applnk/klik/xvier_1.0-7.1.cmg.desktop
/home/th/.kde/share/applnk/.hidden
/home/th/.kde/share/applnk/.hidden/AppRun.desktop
/home/th/.kde/share/mimelnk
/home/th/.kde/share/mimelnk/all
/home/th/.kde/share/mimelnk/all/cmg.desktop
/lib/modules/2.6.12-10-686-smp/kernel/drivers/mtd/mtd_blkdevs.ko
/sbin/blockdev

Could I safely remove the above? If yes, how?

I have nothing against kde which I  would love to try out some day but it's a matter of space on my hd.
Thanks guys!

---

### Post by Qrk on 2006-02-28
Use synaptic to remove the files... don't just delete them.

However, beware. If you use Opera or K3b or some other applications, they will depend on some of these libs. Thats probably why you have them, you installed an application that used qt.

---

### Post by xyz on 2006-02-28
[QUOTE=Qrk]Use synaptic to remove the files... don't just delete them.

However, beware. If you use Opera or K3b or some other applications, they will depend on some of these libs. Thats probably why you have them, you installed an application that used qt.[/QUOTE]

Thanks I'll try this way since I don't use Opera or K3b for now.
If I remember correctly, Synaptic will tell me "if you remove this then it will also uninstall that." So making sure it doesn't uninstall what I do need should keep me on the safe side.

---

### Post by Perfect Storm on 2006-02-28
You could go for gnomebaker instead of kb3 if you don't want kdelibs or qtlibs.

---

### Post by xyz on 2006-02-28
[QUOTE=Artificial Intelligence]You could go for gnomebaker instead of kb3 if you don't want kdelibs or qtlibs.[/QUOTE]
That sounds like a good plan. Thanks for your help A.I. and all of you guys.

---

### Post by shiellb on 2006-03-01
Good evening all.  The last couple of times when I was attempting to complete an automatice update the following appeared in a pop up window - W: Couldn't stat scource package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/multiverse Packages (var/lib/apt/lists/).  What does this mean and what do I do to fix it?  Thanks.

---

### Post by jimrz on 2006-03-01
[QUOTE=shiellb]Good evening all.  The last couple of times when I was attempting to complete an automatice update the following appeared in a pop up window - W: Couldn't stat scource package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/multiverse Packages (var/lib/apt/lists/).  What does this mean and what do I do to fix it?  Thanks.[/QUOTE]

usually means their site was off-line...keep trying it'll get back up eventually

---

### Post by CameronCalver on 2006-03-01
can some1 tell me how to add a thread

---

### Post by handy on 2006-03-03
[QUOTE=CameronCalver]can some1 tell me how to add a thread[/QUOTE]

Choose the appropriate sub-forum carefully, & you will see up at the topish left of the screen the **_New Thread_** link.

---

### Post by shiellb on 2006-03-03
Thank you.

---

### Post by handy on 2006-03-04
Hang in there Bob! 

It becomes very comfortable after a couple of months.  Very steep at the start though! :KS

---

