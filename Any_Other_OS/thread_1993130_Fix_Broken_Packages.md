---
title: "Fix Broken Packages"
date: 2012-06-01
forum: Any Other OS
---

### Post by dontgetshocked on 2012-06-01
I am having a Fix Broken Packages problem.After trying;sudo apt-get update...sudo apt-get -f install...sudo apt-get autoclean...sudo apt-get clean...sudo dpkg --remove -force --force-remove-reinstreq (with package name).Nothing is fixing this.My update manager says that I need to update libcups2 but then I get a broken packages messages.The 2 files that are broken are;libcups2 and libcups:i386 but if I try removing them,it wants to uninstall Banshee and a lot of other software.

Thanks

---

### Post by critin on 2012-06-01
Are you running 12.04?  Did you install Synaptic Package Manager from Software Center?  If not, install it and open it up.  Refresh so it will pick up latest packages.  Along the bottom rim of the manager page look for 'broken packages'  If the notification is there, click on EDIT at the top of the page and choose 'Fix Broken Packages'.

---

### Post by dontgetshocked on 2012-06-01
I am running Mint 13 but I did try synaptic and it is installed by default.I tried using the broken packages filter and it did not work as explained.Thanks

---

### Post by cortman on 2012-06-01
> **dontgetshocked said:**
> I am running Mint 13

Then you should ask in the Mint forums.

But till you do... have you tried

```
sudo apt-get install -f
```

note: *not*

```
sudo apt-get -f install
```

---

### Post by dontgetshocked on 2012-06-01
Since both distros use the same base packages such as synaptic and of course Mint is based on Ubuntu,whatever works on Ubuntu will wok on Mint in this case.This forum also has a wider userbase so I'm staying...Thanks!

---

### Post by oldos2er on 2012-06-01
Moved to Other OS/Distro Talk.

---

