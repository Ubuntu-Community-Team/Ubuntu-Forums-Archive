---
title: "Dapper installed properley?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by joewhite on 2006-06-02
I upgraded to dapper throught the updater but right at the end it got an error. I rebooted and I seem to have dapper anyway but to make sure I edited my sources.list for dapper and did a dist-upgrade. I also did an apt update but it reports the same error

The following packages have been kept back:
  flashplugin-nonfree gdk-imlib1 gnome-cups-manager libopenal0
  python-netcdf

Does this mean these packages haven't been installed right?

---

### Post by johnc4510 on 2006-06-02
This may not work, but is worth a try:
sudo apt-get -f install

---

### Post by carlosqueso on 2006-06-02
[QUOTE=joewhite]I upgraded to dapper throught the updater but right at the end it got an error. I rebooted and I seem to have dapper anyway but to make sure I edited my sources.list for dapper and did a dist-upgrade. I also did an apt update but it reports the same error

The following packages have been kept back:
  flashplugin-nonfree gdk-imlib1 gnome-cups-manager libopenal0
  python-netcdf

Does this mean these packages haven't been installed right?[/QUOTE]

I get the middle 3 packages kept back on mine too....does anyone know about this?

---

### Post by johnc4510 on 2006-06-02
The next thing to try is to enable the universe and multiverse repostories.
System>Administration>Synaptic Package Manager
Click on settings, click on repostories
Put a check in all empty boxes and close that window
Click on reload, click on mark all upgrades, click on apply

---

### Post by joewhite on 2006-06-02
The output of sudo apt-get -f install is: 0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by catlett on 2006-06-02
Usually it means there isn't a newr version to update along with everything else. Try aptitude and see if it deals with the issue.
```
sudo aptitude update 
``````
 sudo aptitude dist-upgrade
``` I guess you could just do a ```
sudo aptitude upgrade
``` since you already upgraded to dapper but it shouldn't matter.

---

### Post by carlosqueso on 2006-06-02
That fixes mine :-D thanks a lot

EDIT:  apt-get bug?

---

### Post by houseshadow on 2006-06-02
I had similar issues, but managed to upgrade the packages manually in Synaptic.  I just located and marked for upgrade.

---

### Post by joewhite on 2006-06-02
Yea that worked. Thanks very much.

---

### Post by catlett on 2006-06-02
[QUOTE=carlosqueso]That fixes mine :-D thanks a lot

EDIT:  apt-get bug?[/QUOTE]
Not a bug just differences in how they deal with packages. They both draw from the repositories. The difference is aptitude will try and resolve dependencies. It will either search for an application that is needed or it will remove an application that is causing an error. Apt-get  will just alert you there is an error or an issue. It doesn't try to resolve anything.
I use aptitude instead of apt-get for everything to do with installing, removing and upgrading.

---

### Post by carlosqueso on 2006-06-04
thanks for the clarification, I may use aptitude from now on.

---

### Post by JeffreyRatcliffe on 2006-06-07
[QUOTE=houseshadow]I had similar issues, but managed to upgrade the packages manually in Synaptic.  I just located and marked for upgrade.[/QUOTE]

Just to confirm this. I had exactly the same problem. I searched for the package name in Synaptic and manually marked them for upgrade.

---

