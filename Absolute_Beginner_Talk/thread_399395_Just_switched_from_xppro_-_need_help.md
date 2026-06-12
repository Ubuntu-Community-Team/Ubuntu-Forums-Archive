---
title: "Just switched from xp/pro - need help"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by colonist on 2007-04-02
I replaced my xp system with dapper drake and have just created an edgy eft cd.  i am not clear on how to upgrade to edgy eft.
I am a linux newbie.

---

### Post by jvc26 on 2007-04-02
I'd check out the upgrade notes: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

To upgrade via the cd you can just do a fresh install of the new version, its a good idea to have a separate /home partition to do this otherwise you'll just end up wiping everything when you delete the partition off the HDD. - Useful guide on setting up a separate /home can be found here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) With a separate /home you can then wipe the main partition (where your dapper install is) and install the new version onto it, and set the /home partition to be mounted as /home (part of the install options, and make sure that this is not re-formatted, thus preserving your data) thus you have a new edgy install, with all your personal files maintained on the /home. As always with updates you need to make sure you have your stuff backed up as a hard copy in case things go wrong and you have to fresh install.
Il

---

### Post by az on 2007-04-02
> **colonist said:**
> I replaced my xp system with dapper drake and have just created an edgy eft cd.  i am not clear on how to upgrade to edgy eft.
I am a linux newbie.

You don't upgrade from the cd.  You upgrade from the internet.

If you want to upgrade form a cd, you would need to use the Alternate cd.  The Alternate cd is different from the Desktop cd in that it contains a repository of packages and not a live cd system.

The thing is that the alternate cd will only provide the packages from main.  Any packages from other repositories still need to be fetched form the internet.

Unless you are on dialup, you really want to just change your sources to the new release and dist-upgrade.  You can have installed a system in 2004 and have kept it up-to-date with the most current release of Ubuntu without ever having bunred another cd.

---

### Post by mikeyphi on 2007-04-02
> **colonist said:**
> I replaced my xp system with dapper drake and have just created an edgy eft cd.  i am not clear on how to upgrade to edgy eft.
I am a linux newbie.

Hi There! 
Two ways - do a clean install using a Edgy iso CD...but this will probably wipe your data! 
OR do an upgrade - look here for instructions [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Don't forget that dapper is long term support - meaning that it will be supported for quite a while. However if you prefer to use the latest (stable) version I suggest an upgrade to edgy now followed by an upgrade to feisty later this month when it is released.

---

