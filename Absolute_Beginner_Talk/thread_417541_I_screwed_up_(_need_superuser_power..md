---
title: "I screwed up :( need superuser power."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-21
HI, I was upgrading from 6.10 to 7.04 today, and while doing that I was multi-tasking. My computer has been running for a few days and while the 7.04 was trying to install onto my PC, my PC shuts down.. I get back on and when I try to go back to the update manager I get nothing on the update list, so I press check and I get this 

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
  
```

So I open a Terminal and type that in ,it tells me 

```

tyler@tyler-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ 

```

I'm new to Linux and I'm very scared, I don't wanna have to reinstall 6.06 ( my original disc ) and update to 6.10 and get 7.04 over again. Please help =(

---

### Post by mills on 2007-04-21
try "sudo dpkg --configure -a"

---

### Post by oilchangeguy on 2007-04-21
try typing sudo at the beginning.

---

### Post by Zaosyn on 2007-04-21
```
tyler@tyler-desktop:~$ sudo dpkg --configure -a
Password:
Setting up xscreensaver-data (4.24-5ubuntu2) ...

Setting up xorg (7.2-0ubuntu11) ...
Setting up brltty (3.7.2-7ubuntu3) ...
Installing new version of config file /etc/init.d/brltty ...
update-initramfs: Generating /boot/initrd.img-2.6.20-15-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.

Setting up vino (2.18.1-0ubuntu1) ...

Setting up xscreensaver-gl (4.24-5ubuntu2) ...

Setting up zenity (2.18.1-0ubuntu1) ...

Setting up libgtk2.0-bin (2.10.11-0ubuntu3) ...
Updating the IM modules list for GTK+-2.10.0...done.
Updating the gdk-pixbuf loaders list for GTK+-2.10.0...done.

Setting up tangerine-icon-theme (0.20-0ubuntu1) ...

Setting up brltty-x11 (3.7.2-7ubuntu3) ...
Setting up scim-gtk2-immodule (1.4.4-7ubuntu1) ...
Updating the IM modules list for GTK+-2.10.0...done.

Setting up gucharmap (1.10.0-0ubuntu1) ...

Setting up tango-icon-theme-common (0.7-0ubuntu1) ...

Setting up ubuntu-desktop (1.43) ...
Setting up scim-modules-table (0.5.6-2) ...
Setting up scim-tables-additional (0.5.6-2) ...
tyler@tyler-desktop:~$ 

``` 
Is what I got afterwards. And I'm no longer getting that error. However when I go to the update manager and press 'check' it's not showing any updates ( well maybe cause I'm uptodate ) but it's not showing that 7.04 distrubution is ready.

---

### Post by riven0 on 2007-04-21
Can you try upgrading again through the update manager? It's probably not completed.

---

### Post by Zaosyn on 2007-04-21
> **riven0 said:**
> Can you try upgrading again through the update manager? It's probably not completed.

Yeah that's what I wanted to do was to go and re-download it and try to reinstall however, it's no longer showing up to download in the Update manager now.

---

### Post by Mike_Longbow on 2007-04-21
Try running update-manager with
```
update-manager -c
```

---

### Post by Zaosyn on 2007-04-21
> **Mike_Longbow said:**
> Try running update-manager with
```
update-manager -c
```

Tried it, and still nothing :(

My computer restarted during the installing process, the one right befor the cleaning process.

---

### Post by Zaosyn on 2007-04-21
WOOT! I was still wondering why it wouldn't work, and to think the very least in my head it was because even though my computer restarted at the very end of the installation there might be some hope I would be running 7.04.

```
tyler@tyler-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ 
tyler@tyler-desktop:~$ 

```

---

### Post by alexj.powell on 2007-06-17
yeah i had the same problem but with a different message
ill try typing that sudo thing in as well...



--
Powell out

---

