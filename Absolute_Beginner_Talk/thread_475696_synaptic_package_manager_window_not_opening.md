---
title: "synaptic package manager window not opening"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by mabbasj on 2007-06-16
I am facing prblem in Ubuntu 6.10.
Whenever i want to open Synaptic Package Manager under System>Administration> it failed to open its windo.Similar problem faced with other applications like Disks under System>Administration etc.
Please help me out i am realy in problem because of this.

Regards
Muzaffar Abbas
Lahore Pakistan

---

### Post by overdrank on 2007-06-16
> **mabbasj said:**
> I am facing prblem in Ubuntu 6.10.
Whenever i want to open Synaptic Package Manager under System>Administration> it failed to open its windo.Similar problem faced with other applications like Disks under System>Administration etc.
Please help me out i am realy in problem because of this.

Regards
Muzaffar Abbas
Lahore Pakistan

Hi have you tried to update through the terminal? Applications, Accessories, Terminal. Use the commands
[I]sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade[/I] 
Hope this helps!:popcorn:

---

### Post by mabbasj on 2007-06-16
but problem is why its graphical interface not working wat problem it is

---

### Post by bapoumba on 2007-06-16
> **mabbasj said:**
> but problem is why its graphical interface not working wat problem it is
Please run **gksudo synaptic** from a terminal and paste the output in here.

---

### Post by whizkid420 on 2008-01-12
hi.. i'm also facing a similar problem... if i enter the command, it prompts for the password and does not open anything,..

\vshah@lgvshah:~$ gksudo synaptic
vshah@lgvshah:~$

---

### Post by bapoumba on 2008-01-12
@ whizkid420: is it installed?
Please paste the output to:
```
aptitude show synaptic
```

If using ubuntu with GNOME, please make sure ubuntu-desktop is installed too.

---

### Post by sandclock on 2008-01-28
Hi
I have same prob ubuntu 7.04 
output u asked is
--------------xx-----------------
Package: synaptic
State: installed
Automatically installed: no
Version: 0.57.11.1ubuntu14
Priority: optional
Section: admin
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5976k
Depends: libapt-inst-libc6.4-6-1.1, libapt-pkg-libc6.4-6-3.53, libatk1.0-0 (>=
         1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.2), libfontconfig1
         (>= 2.4.0), libgcc1 (>= 1:4.1.2), libglade2-0 (>= 1:2.5.1),
         libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3),
         liblaunchpad-integration0 (>= 0.0patch26), libpango1.0-0 (>= 1.16.1),
         libstdc++6 (>= 4.1.2), libvte9 (>= 1:0.16.0), libx11-6, libxcursor1 (>
         1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxft2 (> 2.1.1), libxi6,
         libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0),
         libxrender1, scrollkeeper
Recommends: gksu, deborphan, libgnome2-perl
Suggests: dwww
Conflicts: gsynaptic, menu (< 2.1.11)
Replaces: gsynaptic
Provides: gsynaptic
Description: Graphical package manager
 Synaptic is a graphical package management tool based on GTK+ and APT. Synaptic
 enables you to install, upgrade and remove software packages in a user friendly
 way. 
 
 Besides these basic functions the following features are provided: 
 * Search and filter the list of available packages 
 * Perform smart system upgrades 
 * Fix broken package dependencies 
 * Edit the list of used repositories (sources.list) 
 * Download the latest changelog of a package 
 * Configure packages through the debconf system 
 * Browse all available documentation related to a package (dwww is required)
------------------------xxx--------------------------
any ideas?
Regards
Nik

---

