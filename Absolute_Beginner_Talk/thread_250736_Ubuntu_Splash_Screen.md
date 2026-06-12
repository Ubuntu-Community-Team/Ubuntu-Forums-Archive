---
title: "Ubuntu Splash Screen"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2006-09-04
Hi all,

When I installed the kubuntu pack for KDE and uninstalled I still have the kubuntu splash/boot-up screen. How would I go about going back to the ubuntu one?

-Tanner

---

### Post by whizbaby on 2006-09-04
Did you try **sudo apt-get remove** *kubuntu-artwork-usplash*?

---

### Post by mejy on 2006-09-04
> **TannerLD said:**
> Hi all,

When I installed the kubuntu pack for KDE and uninstalled I still have the kubuntu splash/boot-up screen. How would I go about going back to the ubuntu one?

-Tanner
```

sudo update-alternatives --config usplash-artwork.so
```

Then chose usplash-default.so.

Should work.

---

### Post by TannerLD on 2006-09-04
whizbaby:
It says its not installed.

mejy:
```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```

-Tanner

---

### Post by mejy on 2006-09-04
> **TannerLD said:**
> whizbaby:
It says its not installed.

mejy:
```
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

```

-Tanner

According to that you are already using the Ubuntu usplash.  Perhaps another reboot?

---

### Post by TannerLD on 2006-09-04
Did another quick reboot (love how fast that is) and the kubuntu thing is still there. :\

Thanks
-Tanner

---

### Post by mejy on 2006-09-04
In that case, try [http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash).

It doesn't include instructions to revert to the default Ubuntu USplash, but after following it you should get a better looking Usplash anyway.

---

### Post by TannerLD on 2006-09-04
So, am I stuck with this kubuntu thing that shouldn't exist?

-Tanner

---

### Post by whizbaby on 2006-09-05
If you got enough time to spend on this you can try finding kubuntu-leftovers by:

**cd /**
**sudo grep -r kubuntu . |less**

This will recurse through ALL files and directories on the computer searching for the string 'kubuntu' (file contents are recursed, too, so it'll take a while) and display the output with less (you don't have to type '|less', it's only for overview)

---

### Post by wadetuple on 2006-09-05
hey, i've got a similar thing - when i turn my computer on, i get the kubuntu splash, even though i'm using ubuntu and have never installed kubuntu. it doesn't seem to matter though, the computer goes into ubuntu fine once it's started up...

---

### Post by TannerLD on 2006-09-05
> **whizbaby said:**
> If you got enough time to spend on this you can try finding kubuntu-leftovers by:

**cd /**
**sudo grep -r kubuntu . |less**

This will recurse through ALL files and directories on the computer searching for the string 'kubuntu' (file contents are recursed, too, so it'll take a while) and display the output with less (you don't have to type '|less', it's only for overview)

Looking through it I found somethings like kubuntu-artwork-usplash. Seems something like this:

```

./var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages:Package: kubuntu-artwork-usplash
./var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages:Source: kubuntu-default-settings
./var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages:Filename: pool/main/k/kubuntu-default-settings/kubuntu-artwork-usplash_6.06-21_i386.deb
./var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages:Description: kubuntu artwork for usplash
./var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages: The usplash startup screen for kubuntu.

```

Thanks
-Tanner

---

### Post by whizbaby on 2006-09-05
Helas, these only are package-lists, so no hint about what's on your system, just what could be installed. Were there no other matches?

---

### Post by TannerLD on 2006-09-05
> **whizbaby said:**
> Helas, these only are package-lists, so no hint about what's on your system, just what could be installed. Were there no other matches?

This is basically what is left if I leave out the Firefox/Thunderbird matches.

```
./.bash_history:sudo apt-get remove kubuntu
./.bash_history:sudo apt-get remove kubuntu-artwork-usplash
./.bash_history:sudo apt-get remove kubuntu-artwork-usplash
./.bash_history:sudo grep -r kubuntu . |less
./.bash_history:sudo grep -r kubuntu
./.bash_history:sudo grep -r kubuntu . |less
./.kde/share/config/startupconfig:kcminputrc_mouse_cursortheme="kubuntu"
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcminputrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcminputrc
./.kde/share/config/startupconfigfiles:/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kpersonalizerrc
./.kde/share/config/startupconfigfiles:/usr/share/kubuntu-default-settings/kde-profile/default/share/config/ksplashrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcmrandrrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcmrandrrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcmrandrrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcmrandrrc
./.kde/share/config/startupconfigfiles:!/usr/share/kubuntu-default-settings/kde-profile/default/share/config/kcmrandrrc
./.kde/share/config/kcminputrc:cursorTheme=kubuntu
./.kde/share/apps/kconf_update/log/update.log:2006-08-31T18:32:30 mouse_cursor_theme.upd: Updating kcminputrc:Mouse:cursorTheme to 'kubuntu'

```

-Tanner

---

### Post by TannerLD on 2006-09-06
If it is relavent at all the shutdown screen is the ubuntu screen, not the kubuntu one.

-Tanner

---

### Post by ggilmour on 2006-09-18
Hi All.
I've had the exact same problem and managed to fix it as follows :

```
1. Launch Synaptic
2. Search for the usplash package
3. Mark it for complete removal (at this point synaptic told me it would also remove ubuntu-desktop)

4. Apply the changes.
5. Mark the ubuntu-desktop package for Installation (at this point synaptic told me it was also going to install usplash)

6. Apply the changes.

7. Reboot, and all should be well.
```

-George.

---

### Post by ncappel1 on 2006-09-18
I would like to add that there is a great Howto (install/remove k/x/ed/ubuntu) at: [http://ubuntuforums.org/showthread.php?t=205002](http://ubuntuforums.org/showthread.php?t=205002)

---

