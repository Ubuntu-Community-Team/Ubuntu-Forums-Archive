---
title: "advanced appearance"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by prapanj on 2007-10-29
hi following some thread i did some thing and got an advanced appearance setting option unded system>preferences>
then i followed some other post and the same was replaced by a compizconfig manager.. now when i click the compiz config manager, nothing is actually happening..
I now want my advanced appearance settings back..
what shall i do?

---

### Post by w4ett on 2007-10-29
Remove all of the modified Compiz-Fusion packages you have installed and reinstall the standard Gutsy Compiz Packages.  Try this...in the terminal:

```
sudo echo "Removing old compiz things (ask for sudo password now, so commands won't be interupted later)"
echo "aptitude -y remove" `sudo dpkg -l | egrep '(beryl|emerald|compiz)'| awk '{print $2}'` | sudo bash
```

Than again in the terminal run:

```
sudo aptitude -y update && sudo aptitude dist-upgrade
sudo aptitude install compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-fusion-plugins-unofficial compiz-gnome compiz-plugins compizconfig-settings-manager libcompizconfig-backend-gconf libcompizconfig0 python-compizconfig

```

You should have the standard install back, along with the advanced tab in appearances.

---

