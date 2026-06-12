---
title: "Upgrading confusion.."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by JeanNiBee on 2007-02-21
Hi

I am currently using an older verion of Ubuntu (in the 6.x tree... Dapper I believe it'a called). 

I'm wondering, do I need to actually upgrade via the ISO's every once in awhile to stay fresh or will the automated system upgrades be sufficient for me [via Synaptic]?

My thought was that the 'distro' verions in the iso's are merely for packaging of software and kernels and I'm cool with the auto update, BUT if a major version is released (Ex. Ubuntu 7) then I should probably look at a new ISO install.

Hate to make the comparions but would this be analgous to...

Package updates == Service Pack in windows world.
Major updates (I.e. Ver 6 -> 7) == upgrading NT -> XP

**NOTE:** I'm not talking feature set with those comparisions, just the 'thinking' behind it.

Sorry but I"m still in the Windows mindset after living in it's world forever.

---

### Post by tgalati4 on 2007-02-21
If it works, don't worry about it.  Dapper Drake (6.06.1) will be supported for ~3 years for the desktop version and 5 years for the server version.

If you want to try Edgy or Feisty, find another pc (like a friend's messed up windows machine) and load the live distro and play with the new features.

You may find that the time it takes to reconfigure and customize your machine with a new distro is extensive--it's certainly not automatic.  You may be moving to a distro with more bugs and less stability and then moving back to Dapper because of the stability.

I'm not completely sure of the thinking behind the main Ubuntu distributions.  The goals of the offshoots is pretty clear.

Since disk prices are dropping, put in another drive with several partitions and load as many distros as you like.  That way you are only a grub menu away from Dapper when the newer distros act strange.  At least you will still have access to your data from any distribution--and that is really what counts.

---

### Post by Vivix729 on 2007-02-21
You still need to manually upgrade to the next version of Ubuntu (in this case, Edgy 6.10).  So you would have to upgrade from your Dapper 6.06.  Good thing about this is you DON'T need to burn the iso of the 6.10 version.  Upgrading is fairly simple from the CLI:

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Good luck :)

---

### Post by Obor on 2007-02-21
Going with your windows analogy
```
sudo apt-get update && sudo apt-get upgrade
```
will install all the security fixes etc (i.e service packs)

```

gksu "update-manager -c"
```
Will upgrade you to the next version of OS (i.e from 2000 to xp)

---

### Post by JeanNiBee on 2007-02-21
Thanks all for the explanations and tips.

---

### Post by macogw on 2007-02-21
and don't go from Dapper to Edgy on CLI.  The page he linked to even says that CLI is not recommended.  A lot of us had breakage from it.  The gksu "update-manager -c" brings up a modified updater window with a "move to 6.10" button--that actually works

---

### Post by geezerone on 2007-02-21
Would it be possible and safer to upgrade from Dapper to Edgy Eft using a live iso CD?

---

