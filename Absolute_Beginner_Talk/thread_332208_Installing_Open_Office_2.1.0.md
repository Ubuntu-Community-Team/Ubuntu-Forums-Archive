---
title: "Installing Open Office 2.1.0"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-01-05
All,
I am having real problems with the version of Open Office in Ubunto 6.06. It is buggy and locks up every time I try to do some real work. To that end I have downloaded the 2.1 to my desktop. The file I have is **OOo_2.1.0_LinuxIntel_install_en-US.tar.gz**. When I click on it I am asked where to extract.

How do I install this? I have seen some command line stuff in the forums, but as I am a real newbie, I would prefer to install from the desk with point and click.

Thx for the help

---

### Post by taurus on 2007-01-05
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
```
Then, there is an installer that you can run to install it on your machine...

---

### Post by dann0 on 2007-01-05
Does that update/replace the current OOo,
or will I have two versions installed?

---

### Post by Real Newbie on 2007-01-05
By golly that worked like a charm, I think. It didn't crash my computer and require a reinstall like my last attempt to fix my screen resolution.

After extracting the files I went **>Applications>Add/Remove**

I think that this installed 2.1. The issue is when I go **Applications>Office>Open Offic**e

It still opens 2.0.2. How do I replace 2.0.1 with 2.1 on the menu?

Thx

---

### Post by rev_b on 2007-01-05
Not that easy. The tar.gz file is just a packed rpm's archive.
My advice on OOo 2.1 instalation in edgy:

Uninstall OOo 2.0.4 first. Start  synaptic and just search everything with openoffice in it and carefully uninstall a package at once. If it gives an error, just move to the next, you'll eventually be able to uninstall them all. Don't mind about uninstalling ubuntu/kubuntu-desktop in the process, it's a metapackage.

Make sure you got alien installed, as it allows you to install .rpm packages. If not, just search for alien in synaptic and install it.

Extract OOo_2.1.0_LinuxIntel_install_en-US.tar.gz. In the terminal, go to the folder RPM and run the command: $ sudo alien -i -s *.rpm

It'll automatically convert rpm files to deb package format and install them. It'll take a while. 

Then go to the folder /RPMS/desktop-integration and install openoffice.org-debian-menus_2.1-*_all.deb. You may do it from with nautilus double clicking it, or running $ sudo dpkg -i openoffice.org-debian-menus_2.1-*_all.deb from the command line. Make sure you install openoffice.org-debian-menus_2.1-*_all.deb last, or you won't get all OOo apps in the menus.

There, you should have OOo 2.1 installed and with new menu entries in Applications -> office.

---

### Post by NumberOne on 2007-01-05
I used the info from this post and worked for me

[http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=openoffice+2.1](http://www.ubuntuforums.org/showthread.php?t=318865&page=3&highlight=openoffice+2.1)

---

### Post by Real Newbie on 2007-01-05
Then what did **>Applications>Add/Remove** do if it didn't install?

Thx

---

### Post by Real Newbie on 2007-01-05
Allright...
I have gotten to the part

**In the terminal, go to the folder RPM.**

I am in the terminal
How do I go to a folder?

Thx

---

### Post by Real Newbie on 2007-01-05
OK, I figured that one out. I just typed RPM and I think I think I went to the folder. I got

RPM version 4.4.1
Copyright (C) 1998-2002 - Red Hat, Inc.
This program may be freely redistributed under the terms of the  GNU GPL

Usage: rpm [-a|--all] [-f|--file] [-g|--group] [-p|--package] [ -W|--ftswalk]
        [--pkgid] [--hdrid] [--fileid] [--specfile] [--triggere dby]
        [--whatrequires] [--whatprovides] [--nomanifest] [-c|-- configfiles]
        [-d|--docfiles] [--dump] [-l|--list] [--queryformat=QUE RYFORMAT]
        [-s|--state] [--nomd5] [--nofiles] [--nodeps] [--noscri pt]
        [--comfollow] [--logical] [--nochdir] [--nostat] [--phy sical]
        [--seedot] [--xdev] [--whiteout] [--addsign] [-K|--chec ksig]
        [--delsign] [--import] [--resign] [--nodigest] [--nosig nature]
        [--initdb] [--rebuilddb] [--aid] [--allfiles] [--allmat ches]
        [--badreloc] [-e|--erase <package>+] [--excludedocs]
        [--excludepath=<path>] [--fileconflicts] [--force]
        [-F|--freshen <packagefile>+] [-h|--hash] [--ignorearch ] [--ignoreos]
        [--ignoresize] [-i|--install] [--justdb] [--nodeps] [-- nomd5]
        [--nocontexts] [--noorder] [--nosuggest] [--noscripts]
        [--notriggers] [--oldpackage] [--percent] [--prefix=<di r>]
        [--relocate=<old>=<new>] [--repackage] [--replacefiles]
        [--replacepkgs] [--test] [-U|--upgrade <packagefile>+]
        [-D|--define 'MACRO EXPR'] [-E|--eval 'EXPR'] [--macros =<FILE:...>]
        [--nodigest] [--nosignature] [--rcfile=<FILE:...>] [-r| --root ROOT]
        [--querytags] [--showrc] [--quiet] [-v|--verbose] [--ve rsion]
        [-?|--help] [--usage] [--scripts] [--setperms] [--setug ids]
        [--conflicts] [--obsoletes] [--provides] [--requires] [ --info]
        [--changelog] [--triggers] [--last] [--filesbypkg] [--f ileclass]
        [--filecolor] [--filecontext] [--fscontext] [--recontex t]
        [--fileprovide] [--filerequire] [--redhatprovides]
        [--redhatrequires] [--buildpolicy=<policy>] [--with=<op tion>]
        [--without=<option>]

That seems to tell me that I am in RPM. I then typed

**sudo alien -i -s *.rpm**

and got

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
You can not use --generate or --single with --install.

What now?

Thx

---

### Post by Real Newbie on 2007-01-05
Could someone take a quik look. I need to get over this hump and I am stuck.

Thx

---

### Post by rev_b on 2007-01-05
> **Real Newbie said:**
> Allright...
I have gotten to the part

**In the terminal, go to the folder RPM.**

I am in the terminal
How do I go to a folder?

Thx

with the cd command. If you extracted the file to your Desktop, it'll be

cd ~/Desktop/OOE680_m6_native_packed-1_en-US.9095/RPMS

Note: you can copy text from firefox and paste it on a terminal using the middle mouse button or pressing shift+insert

---

