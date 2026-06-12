---
title: "upgrade without using atp-get"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by zanfry on 2006-10-18
Hi!! I should upgrade from Breezy Badger to Dapper. Does exist any CD ISO or pkg that I can download, without using atp-get?

---

### Post by ReaderRat on 2006-10-18
> **zanfry said:**
> Hi!! I should upgrade from Breezy Badger to Dapper. Does exist any CD ISO or pkg that I can download, without using atp-get?
ISO - Downloading & Burning
          [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)
          [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[**(X/K)Ubuntu Download**](http://www.ubuntu.com/)

---

### Post by velo on 2006-10-18
This little HOWTO might help you finding out which images to download and what to change when upgrading using a CD as a Package source: [https://help.ubuntu.com/community/DapperUpgrades#head-1596eecf4b58a03b3d9f44172a661382f8065a58](https://help.ubuntu.com/community/DapperUpgrades#head-1596eecf4b58a03b3d9f44172a661382f8065a58)

---

### Post by Brunellus on 2006-10-18
If the computer is connected to the internet, apt is the preferred means of updating.

---

### Post by zanfry on 2006-10-18
I thank everyone; I'm connected with 56k, so I gotta download the upgrade on another PC with Win as OS

---

### Post by zanfry on 2006-10-18
If it's possible, I'd like to download the upgrade pkgs only, instead of the whole dapper, and then I'd transfer 'em to Ubuntu instal them

---

### Post by Brunellus on 2006-10-18
> **zanfry said:**
> If it's possible, I'd like to download the upgrade pkgs only, instead of the whole dapper, and then I'd transfer 'em to Ubuntu instal them
probably not a good idea.  If you're that desperate, get an install CD of the version you want to upgrade TO (e.g. dapper).  Change all references in /etc/apt/sources.list to point to 'dapper' rather than 'breezy'--INCLUDING the CD line, which may or may not be commented out.

Then insert the CD, sudo apt-get update, sudo apt-get dist-upgrade.

Note that this will only upgrade the core packages that came on the CD, not any other packages you may have installed in the meantime.

---

### Post by zanfry on 2006-10-19
Thank you!

---

### Post by zanfry on 2006-10-20
Then, if I've unterstood, there's no way to download just the  pkgs Breezy lacks using the connection of another OS?

---

### Post by CatKiller on 2006-10-20
> **zanfry said:**
> Then, if I've unterstood, there's no way to download just the  pkgs Breezy lacks using the connection of another OS?

There is, but it's complicated enough not to bother. You'd need to get all the dependencies of each package that you need to install, and the dependencies of each dependency, and so on, and then line them up in the appropriate manner on the cd to be able to add it as a repository, and even then you'll probably have missed something and it won't work.

As an alternative, you could take the computer somewhere with broadband, network the computer in, and download the packages from the Internet that way.

---

### Post by zanfry on 2006-10-21
thank every-one. I'm gonna find  magazine with ubuntu in attachment..

---

