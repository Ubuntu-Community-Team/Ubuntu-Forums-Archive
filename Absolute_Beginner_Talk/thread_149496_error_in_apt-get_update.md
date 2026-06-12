---
title: "error in apt-get update"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-03-24
hi, my problem is when i do "sudo apt-get update" y get this error
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/universe/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/multiverse/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/universe Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by dermotti on 2006-03-24
I thinks its giving that error because you have the cd-rom enabled as a repository, and you do not have the ubuntu disc in your cdrom drive. You could just disable the cd-rom repos within synaptic.

---

### Post by bluevoodoo1 on 2006-03-24
Or open your /etc/apt/sources.list file and put a # in front of the lines that deal with your CDrom

```
sudo gedit /etc/apt/sources.list
```

then it should look like this...
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

Save file. Then 'sudo apt-get update'

---

