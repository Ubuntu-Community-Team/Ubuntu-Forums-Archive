---
title: "Cube stops working then I lose borders"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by ssharps711 on 2008-02-06
So my borders were gone (can'tr move windows with click+drag) and I did a 

```
compiz --replace
```

That restores borders but I lose control of my cube. No cube.

So I enter 

```
metacity --replace
```

and I lose the borders again. Soooo do I want my borders? Or a sweet *** cube.... Damn I wish I could have both.

Alt+click moves my windows.

---

### Post by ssharps711 on 2008-02-06
When I enter ```
metacity --replace
```

I get

> Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by ssharps711 on 2008-02-06
Bump

---

### Post by ssharps711 on 2008-02-06
Bump. C'mon man. Help me out. Someone has to know something. Any suggestions.

---

### Post by Charcoal1981 on 2008-02-06
Go to the gnome configuration editor:
```
gconf-editor
```
Browse to "apps>metacity>window_keybindings" and check the value given for "toggle_shaded"
It reads "disabled" on my system. Set it to disabled or give it a keyboard shortcut.

If that doesn't work, what effects do you have enabled under compiz??

---

### Post by ssharps711 on 2008-02-06
Should I reboot after I edit those settings? I just put it to disabled.

Then entered

 ```
master@master-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Now neither the cube nor the windows are moving even with <Alt+click+drag>.

XGL is gone.

Also, my windows seem to to be stuck, can't bring anything forward and my Kiba dock is trailing the icons. 

It's MESSED up.

I have an i810 driver.

---

### Post by ssharps711 on 2008-02-06
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
# deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
# deb http://flomertens.keo.in/ubuntu/ edgy main main-all
# deb http://mirror.ubuntulinux.nl edgy-seveas all

# deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

deb http://download.tuxfamily.org/3v1deb **feisty** eyecandy
deb-src http://download.tuxfamily.org/3v1deb **feisty** eyecandy
```

It's feisty eye candy... That could be a problem no?

---

### Post by Charcoal1981 on 2008-02-06
It should not require a reboot. There is obviously something more serious wrong with your setup. I don't understand why Xgl is not present (or at least not detected) - is it installed? If not:

```
sudo apt-get install xserver-xgl
```

I assume you have had things working correctly previously, what alterations did you make prior to it stopping?? Does your system work correctly if desktop effects are disabled?

---

### Post by Charcoal1981 on 2008-02-06
> **ssharps711 said:**
> ```

...
deb http://download.tuxfamily.org/3v1deb **feisty** eyecandy
deb-src http://download.tuxfamily.org/3v1deb **feisty** eyecandy
```

It's feisty eye candy... That could be a problem no?

Sorry missed that post. It could be. what version are you actually running?? You seem to have edgy and fiesty repositories enabled...

---

### Post by ssharps711 on 2008-02-06
Gutsy.

I installed edgy last week, then upragraded to fesity then gusty.

Yes, xgl was working fine. It was all good until like yesterday. I have no clue what happened.

---

### Post by ssharps711 on 2008-02-06
Did ```
master@master-desktop:~$ sudo apt-get install --reinstall compizconfig-settings-manager
[sudo] password for master:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compizconfig-settings-manager
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/611kB of archives.
After unpacking 487kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  compizconfig-settings-manager
Install these packages without verification [y/N]? y
(Reading database ... 163900 files and directories currently installed.)
Preparing to replace compizconfig-settings-manager 0.5.2+git20070912-0ubuntu1 (using .../compizconfig-settings-manager_0.6.99~git20071005+3v1ubuntu0_i386.deb) ...
Unpacking replacement compizconfig-settings-manager ...
Setting up compizconfig-settings-manager (0.6.99~git20071005+3v1ubuntu0) ...
master@master-desktop:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
master@master-desktop:~$ kgedit /etc/apt/sources/list
bash: kgedit: command not found
master@master-desktop:~$ kgedit /etc/apt/sources.list
bash: kgedit: command not found
master@master-desktop:~$ sudo gedit /etc/apt/sources.list
master@master-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 1737kB of archives.
After unpacking 4510kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe xserver-xgl 1:1.1.99.1~git20070727-0ubuntu3 [1737kB]
Fetched 1737kB in 17s (98.9kB/s)                                               
Selecting previously deselected package xserver-xgl.
(Reading database ... 163952 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_1%3a1.1.99.1~git20070727-0ubuntu3_i386.deb) ...
Setting up xserver-xgl (1:1.1.99.1~git20070727-0ubuntu3) ...
```

Then still```
master@master-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

I don't have an Nvidia... Just ignore that?

---

### Post by Charcoal1981 on 2008-02-06
Well I think the first thing you probably want to do is sort out your sources list. The easiest way is via "system>administration>software sources" on your main menu and making sure only gusty repositories are selected. When that's sorted you could try reinstalling compiz.

The thing is, with all those conflicting repo's you could have any number of things wrong (e.g. a broken dependancy). If you only installed a week ago, It might be easier just to do a fresh install of gusty (compiz is enabled out of the box).

---

### Post by petersonjacob on 2008-02-06
i had this problem too and i solved it by opening my desktop effects (compiz) went to the window decoration tab and typed in the name of my replacement program (so i typed in "emerald" in the command box)for you maybe metacity or something

---

