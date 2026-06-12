---
title: "upgrade from feist to gutsy"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by tonym53 on 2007-10-09
if you have an internet connection can yo upgrade from feisty fawn to
gutsy when it arrives soon or do you have to burn gutsy on a new cd
or dvd?If so how do you do upgrade online?

---

### Post by PmDematagoda on 2007-10-09
You can upgrade using:-

```
sudo apt-get update -d
```

But be careful, there are no assurances that the upgrade will work perfectly so be prepared to face some problems.

---

### Post by tonym53 on 2007-10-09
thanks for speedy reply

---

### Post by freesitebuilder on 2007-10-09
I've bookmarked this page for the big occasion :)
[http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/](http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/)

---

### Post by goodboyCerberus on 2007-10-09
> **SD-Plissken said:**
> IMHO your best off backing up everything deemed important, As well as any of the config files you edited, and install clean.
You should make backups regardless of what method (upgrade vs fresh install) you choose.

---

### Post by clancymf on 2007-10-09
By backups is there a restore point feature in Ubuntu or should we just back up the data seperately.

Thanks,

---

### Post by phr0ze on 2007-10-09
> **PmDematagoda said:**
> You can upgrade using:-

```
sudo apt-get update -d
```

But be careful, there are no assurances that the upgrade will work perfectly so be prepared to face some problems.

If you are waiting until the official release you do not need to do this. This is for getting the beta release.  The instuctions are here: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

Bascially, here is the text to answer your question.

[SIZE="4"]**Network upgrade for Ubuntu desktops (recommended)**[/SIZE]
When Ubuntu 7.10 is officially released, you can easily upgrade over the network with the following procedure. 

[LIST]
[*]Open System/Administration/Update Manager 

[*]Click the Check button to check for new updates 

[*]A message will appear informing you of the availability of the new release 

[*]Click Upgrade 

[*]Follow the on-screen instructions
[/LIST]

John.

---

### Post by goodboyCerberus on 2007-10-09
> **clancymf said:**
> By backups is there a restore point feature in Ubuntu or should we just back up the data separately.
I meant separately / manually. (My networked external hard drive is a godsend.) I'm not aware of a restore point feature, but I'm just a newbie; you can always use the live cd to check that your desired programs still work. :-)  A roll-back (downgrading packages, finding your old video card drivers, etc) is doable but *manual*, thus I wouldn't recommend it.

---

