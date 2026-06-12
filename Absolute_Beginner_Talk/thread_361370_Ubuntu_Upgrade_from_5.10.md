---
title: "Ubuntu Upgrade from 5.10"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2007-02-14
People,

How do I perform an upgrade?  I mean, I don't want to perform a full installtion, meaning partition formatting, data loss, etc.  I went to [http://www.ubuntulinux.org]("http://www.ubuntulinux.org") and I couldn't find instructions to perform an upgrade.  I could only find full installations, CD-ROM ISOs, etc.

---

### Post by Anicka on 2007-02-14
In the terminal, type:

gksu "update-manager -c"

It should upgrade to one version higher. Thereafter (when you have fixed any problems you might encounter) you can decide how far to go.

---

### Post by oilchangeguy on 2007-02-14
you didn't say if you have a cd for a newer version. and if you do, simply insert the cd, and when prompted to partition the harddrive select the option to allow the new version to take over the entire drive. or (i'm not sure about this part) select the option to allow for an upgrade. in windows if you insert a cd while the old os is running you'll be asked if you want to upgrade to the newer version.

---

### Post by Anicka on 2007-02-14
Some links...

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Good luck!

---

### Post by infol on 2007-02-14
be aware that if you do a distro upgrade, you might break dependancies (especially if you have compiled programs (or kernel) from source rather than installing everything trhough synaptic, or apt-get).

with that said, you will need to configure you /etc/apt/sources.list, and replace all instances of 'hoary' with 'dapper'.

then run ```
sudo apt-get update
sudo apt-get dist-upgrade
```

then, you'll have to wait....for it to finish

---

### Post by paulozzzz on 2007-02-14
I see.  That's why I have been told to install /HOME to a separate partition.  :oops: 

But thanks for the help!  :)

---

### Post by paulozzzz on 2007-02-14
> **oilchangeguy said:**
> you didn't say if you have a cd for a newer version. and if you do, simply insert the cd, and when prompted to partition the harddrive select the option to allow the new version to take over the entire drive. or (i'm not sure about this part) select the option to allow for an upgrade. in windows if you insert a cd while the old os is running you'll be asked if you want to upgrade to the newer version.

I don't have the CD, but I can dl the ISO.

---

### Post by paulozzzz on 2007-02-14
> **Anicka said:**
> Some links...

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Good luck!

Thanks, Anicka,  I'll check them out.

---

### Post by paulozzzz on 2007-02-14
> **Anicka said:**
> Some links...

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Good luck!

Except for the OpenOffice packages I downloaded and installed everything using the update manager.  Reboot.  System seems like before.  :confused: My Ubuntu seems to be still 5.10. 

I am trying to install MDAC to work under WINE.  But the version compatible with 5.10 has a bug that has been fixed by another that requires at least 6.06 ([http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")).

Synaptic insists that the latest WINE version is 20050725.  I would expect that after an upgrade to Edgy, Synaptic would display that there is a newer version of WINE.

Well, then I decided to get to the WINE's home page to get manual installation instructions, and they tell us to run the following shell command:

**wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -**

OUTPUT: **gpg: no valid OpenPGP data found.**

I don't know what I am doing wrong...:confused: :confused: :confused:

---

### Post by paulozzzz on 2007-02-15
Bumping for help.

---

### Post by paulozzzz on 2007-02-15
People, never mind the problem above.  That was due to a proxy.  The WineHQ guys forgot to include instructions to download via a proxy server.

---

