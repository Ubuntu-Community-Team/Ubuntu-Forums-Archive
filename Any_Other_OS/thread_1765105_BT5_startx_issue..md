---
title: "BT5 startx issue."
date: 2011-05-22
forum: Any Other OS
---

### Post by redcodefinal on 2011-05-22
Hi!
Those of you in the security world know that Backtrack 5 just got released on the 10th. I was pretty ecstatic to install it however, when I run the startx command, things take a horrible turn. When I run startx my screen turns black momentarily before coming back to the console. I receive these errors courtesy of the X window system.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux bt 2.6.38 #1 SMP Thu Mar 17 20:52:18 EDT 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38 root=UUID=b04bcd08-65f9-41cb-90b2-fd7b9a9753dc ro text splash nomodeset vga=791
Build Date: 08 March 2011  08:22:50AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.16.4
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 22 12:53:20 2011
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) [drm] failed to open device
(EE) VESA(0): No valid modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```

The BT forums have given me little to no help. I have helped contribute to the Ubuntu forums before so I hoped you all would be able to help me. I have tried a couple fixes, none worked.

1. First, people kept telling em to run fixvesa or fix-vesa. Neither exist on my computer or in any package. If you have any insight on how to get this tool that would be great.

2. I was told to run these commands but, they too didn't fix my problems. 

```

rm /root/.kde/cache-root/icon-cache.kcache
rm /root/.kde/cache-root/plasma_theme_Volatile.kcache
rm /root/.kde/cache-bt/icon-cache.kcache
rm /root/.kde/cache-bt/plasma_theme_Volatile.kcache

```

3. I also deleted and reinstalled all my nVidia drivers, nothing happened yet again.

Specs:
It is a laptop computer, a Dell Insprion 5160 to be exact. IT has 2GB of RAM, a wireless card and apparently nVidia graphics.

Also: I have had this problem with both the KDE version and the GNOME version.

---

