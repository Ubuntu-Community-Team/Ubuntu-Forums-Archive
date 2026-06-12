---
title: "Problems with Updating to Ubuntu 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Crystobal on 2007-10-22
Hello everyone 

I am trying to update to 7.10 from 7.04 Festy but i keep getting this message.

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

I tried to install  the new version via CD but it jams to the step of the Key Board, so can anymone help me with upgrading, is there a way to update without reinstalling the hole thing?

Julie

---

### Post by LanDan on 2007-10-22
> **Crystobal said:**
> Hello everyone 

I am trying to update to 7.10 from 7.04 Festy but i keep getting this message.

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

I tried to install  the new version via CD but it jams to the step of the Key Board, so can anymone help me with upgrading, is there a way to update without reinstalling the hole thing?

Julie

you need to replace the name feisty with gutsy in your sources list, all of them

---

### Post by houstonbofh on 2007-10-22
> **LanDan said:**
> you need to replace the name feisty with gutsy in your sources list, all of them

**Noooooooo**! :eek:  This is not the recommended way to do it, and it **will not** solve your problem. (But it will give you some new ones)

First you can use a Gutsy CD to upgrade.  Browse the CD to the cdupgrade script.

But your problem is that the repoes are hammered right now, and things are slow.  It will get better, but the cdupgrade will be faster anyway.

---

### Post by Seisen on 2007-10-22
Check this out

[https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29%7C%28upgrades%29]("https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29%7C%28upgrades%29")

---

### Post by ThrobbingBrain66 on 2007-10-22
> **houstonbofh said:**
> **Noooooooo**! :eek:  This is not the recommended way to do it, and it **will not** solve your problem. (But it will give you some new ones)

First you can use a Gutsy CD to upgrade.  Browse the CD to the cdupgrade script.

But your problem is that the repoes are hammered right now, and things are slow.  It will get better, but the cdupgrade will be faster anyway.

Only some are being hammered right now.  If you choose "select best mirror" from System > Administration > Software Sources > Download mirror > Other you can get a normal speed upgrade.

---

### Post by LanDan on 2007-10-22
> **houstonbofh said:**
> **Noooooooo**! :eek:  This is not the recommended way to do it, and it **will not** solve your problem. (But it will give you some new ones)

First you can use a Gutsy CD to upgrade.  Browse the CD to the cdupgrade script.

But your problem is that the repoes are hammered right now, and things are slow.  It will get better, but the cdupgrade will be faster anyway.

no?

did something change since debian?

---

### Post by houstonbofh on 2007-10-22
> **LanDan said:**
> no?

did something change since debian?
No.  Everything is **exactly** the same. ;)

Quite a lot, actually.  update-manager will download a bunch of helper scripts first.  It will try and clean up your repos so 3rd party repos don't break everything totally.  It will also grab the default applications that come with the new distribution that were no included in the prior distribution (compiz-fusion for example) and configures them.  It does a **huge** amount of work behind the scenes.

---

