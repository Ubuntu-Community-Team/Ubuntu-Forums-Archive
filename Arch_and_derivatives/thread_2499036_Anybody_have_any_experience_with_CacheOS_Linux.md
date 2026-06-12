---
title: "Anybody have any experience with CacheOS Linux?"
date: 2024-07-08
forum: Arch and derivatives
---

### Post by 909mjolnir on 2024-07-08
I was gonna try CacheOS Linux but I chickened out.  Anybody have any experiences with it?

---

### Post by Rubi1200 on 2024-07-09
I think you mean CachyOS.

Tried and failed with installation, no errors, just failed.

I don't feel like fighting with installs these days; either it works or it doesn't.

However, I do highly recommend EndeavourOS. Smooth as silk, no issues with updates/upgrades, has some nice features.

---

### Post by 909mjolnir on 2024-07-11
Thanks.

---

### Post by currentshaft on 2024-07-11
They signed the ISO image instead of the SHA256 sums with PGP. But the OS has "a focus on security, privacy, and peace of mind." ... yeah, I don't think these developers are very experienced.

---

### Post by #&amp;thj^% on 2024-07-11
> **909mjolnir said:**
> I was gonna try CacheOS Linux but I chickened out.  Anybody have any experiences with it?

It's one of my go to's:
```
NAME="CachyOS Linux"
PRETTY_NAME="CachyOS"
ID=cachyos
ID_LIKE=arch
BUILD_ID=rolling
ANSI_COLOR="38;2;23;147;209"
HOME_URL="https://cachyos.org/"
DOCUMENTATION_URL="https://wiki.cachyos.org/"
SUPPORT_URL="https://forum.cachyos.org/"
BUG_REPORT_URL="https://github.com/cachyos"
PRIVACY_POLICY_URL="https://terms.archlinux.org/docs/privacy-policy/"
LOGO=cachyos

```

They have 2 different repos for newer hardware ie:
```
Active pacman repo servers in: /etc/pacman.d/cachyos-mirrorlist
    1: https://cdn-1.cachyos.org/$arch/$repo
    2: https://us.cachyos.org/repo/$arch/$repo
    3: https://mirror.fast0ne.com/repo/$arch/$repo
    4: https://cdn.cachyos.org/repo/$arch/$repo
    5: https://aur.cachyos.org/repo/$arch/$repo
    6: https://mirror.cachyos.org/repo/$arch/$repo
    7: https://mirror.albony.xyz/cachylinux/repo/$arch/$repo
    8: https://kr.cachyos.org/repo/$arch/$repo
    9: https://mirror.lesviallon.fr/cachy/repo/$arch/$repo

```
For only v3 repos, much newer machines AMD Intel will take v4 which is decided by the installer.

---

### Post by #&amp;thj^% on 2024-07-11
> **currentshaft said:**
> I don't think these developers are very experienced.

His credentials are very high, please only facts, I appreciate thoughts but they are just that "Thoughts"

---

### Post by 909mjolnir on 2024-07-11
my install failed too.

---

### Post by #&amp;thj^% on 2024-07-11
for that: [https://discuss.cachyos.org/categories](https://discuss.cachyos.org/categories)

There is always a log from the installer...."install failed" means nothing to me

```
sudo less /var/log/Calamares.log >calamares-installer.txt

```

---

### Post by 909mjolnir on 2024-07-13
okay, maybe I'll give it another try.

---

### Post by 909mjolnir on 2024-08-27
I decided to go with a different Linux instead of CachyOS

---

