---
title: "upgrade install problem"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by noswal on 2008-04-13
I came back to ubuntu this weekend after a 2 year gap, as I had some files/media to look at. Having upgraded the pc, I got over the problem of getting it to see my screen. I have breezy badger. Encountering problems of what seems an unstable version and currently cannot get internet access due to pc upgrage (wont see network card) I want to upgrade - to gutzy, so as a start..."Skipping versions is not advised and can cause a lot of damage to your installation" I'm trying to go from 5.10 to 6.06

I seem to got over a problem of my cd/dvd drive not working, so I can put a disk in and it reads it, however following [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades) and updating sources.list
I dont seem to get any further. I have unbuntu-6.06.1-desktop-i386.iso on a cd, I can view the files by opening it but runing any command  if I have it correct does nothing.

#To install from a physical CD
   1.      Run:                 sudo apt-cdrom add 

            Insert the CD, and press enter.
  
returns 
E: Failed to mount the cdrom

---

### Post by Diabolis on 2008-04-13
It will be easier and faster to download and burn the gutsy .iso.

---

### Post by Oldsoldier2003 on 2008-04-13
> **Diabolis said:**
> It will be easier and faster to download and burn the gutsy .iso.

yes I agree, pluss it makes the future upgrade path a lot easier.

---

### Post by joshrobinson on 2008-04-13
> **Diabolis said:**
> It will be easier and faster to download and burn the gutsy .iso.

upgrading an old version to a new version can be weird, so if you want to upgrade to Gutsy gibbon, you can only upgrade from Feisty fawn (7.04)

id recommend backing up your data, and just doing a fresh install

but if you wana upgrade, you can only upgrade to the version in front of you
check out this page 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion")

---

### Post by Oldsoldier2003 on 2008-04-13
> **joshrobinson said:**
> upgrading an old version to a new version can be weird, so if you want to upgrade to Gutsy gibbon, you can only upgrade from Feisty fawn (7.04)

id recommend backing up your data, and just doing a fresh install

but if you wana upgrade, you can only upgrade to the version in front of you
check out this page 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion")

I'm pretty sure he was implying a fresh installation but your point is valid. although dapper to hardy will be a valid upgrade path, the devs have stated that there will be a direct upgrade between LTS releases.

---

### Post by joshrobinson on 2008-04-13
> **Oldsoldier2003 said:**
> I'm pretty sure he was implying a fresh installation but your point is valid. although dapper to hardy will be a valid upgrade path, the devs have stated that there will be a direct upgrade between LTS releases.

the OP said they are running breezy badger, not dapper at the moment, they said they have a dapper cd.. and by the look of the commands in the original post, the op is trying to add the dapper repo's into breezy to do an upgrade
so a direct LTS upgrade wont work, unless the upgrade to dapper goes without a hitch

as for me quoting diabolis when he/she said to download the gutsy cd, that was because the op said they wanted to UPGRADE to gutsy, unless the really meant they dont mind doing a new installation, that im not sure of

---

### Post by noswal on 2008-04-14
Well as I read in the doc its best to upgrade from one to the other, however my main problem is how to get my existing set up to accept the disk I have, what commands I need to issue to make it read the disk and install....

---

### Post by noswal on 2008-04-14
Ok, after much fiddling around I gave up and went to do clean install, only problem I initially ran into was X server not found, but with grapics option on boot up install menu that solved that and now have dapper runing (updated profile) with internet etc., which was my main problem and so I'm happy.


I'll run on this for now and install the new hardy once released.


 So, case closed

---

