---
title: "Upgrading from 7.04 to 7.10(Gusty Gibbon)"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-06
I was wondering if I will have to uninstall 7.04 to upgrade to 7.10.  The reason i ask this is that in another post some said to wait to install gusty gibbon.  I would think that this upgrade(7.04 -> 7.1) would not have to be a reinstall, just something that i could upgrade while in Ubuntu automatically.  If someone could explain how upgrading like this(and major versions like 6 -> 7) works that would be great.

---

### Post by shad0w_walker on 2007-10-06
I would recommend the average user to wait for the final release before upgrading, there are very few bugs but theres still the odd one that causes trouble for even some more experience users. When its released you should be able to upgrade using the update-manager (I can't remember if it automatically offers the option or if you have to request)

If you really want to upgrade now you should be able to do so using this command:

```
gksu update-manager -d
```

Be warned its recommend you know what you are doing to run a development release.

---

### Post by asmoore82 on 2007-10-06
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Pumalite on 2007-10-06
You can upgrade, but upgrades are messy and sometimes not very lucky. If I were you, I'd save data and do a clean install.

---

### Post by pilot_guy415 on 2007-10-06
Yes you can upgrade from the update manager. Just remember that 7.10 is still in beta.

Open the terminal and type

```
update-manager -d
```

This will open your update manager and tell you that you can upgrade to 7.10 follow that instructions and your all set. Be warned though, it took me like 5 hours to download/upgrade...dont know if thats common or not :confused:

---

### Post by Daveth on 2007-10-06
I guess the "wait for it" comment hinged more on the beta status of Gutsy than anything else. I'll certainly wait a little while even after it is out, just to make sure it plays nice (which I'm sure it will):).

---

### Post by cameronol on 2007-10-26
Does upgrading from 7.04 to 7.10 delete my files and/ or themes and custom upgrades?

---

### Post by Pumalite on 2007-10-26
If your question is 'will it mess up my system?' Look around. This is a turkey shoot. I will save data and do a clean install. (as I have done in my computers; two Beta installs that I updated to Final Release without a problem. Three installs with Final Gutsy without a hitch.)

---

### Post by cameronol on 2007-10-26
thanks
:guitar:

---

### Post by Crafty Kisses on 2007-10-26
> **Pumalite said:**
> If your question is 'will it mess up my system?' Look around. This is a turkey shoot. I will save data and do a clean install. (as I have done in my computers; two Beta installs that I updated to Final Release without a problem. Three installs with Final Gutsy without a hitch.)

That's true.

---

