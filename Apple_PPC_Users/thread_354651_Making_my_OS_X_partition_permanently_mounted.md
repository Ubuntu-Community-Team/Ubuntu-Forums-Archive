---
title: "Making my OS X partition permanently mounted"
date: 2007-02-06
forum: Apple PPC Users
---

### Post by galvatron1983 on 2007-02-06
Im working from a fresh install of Kubuntu 6.10 PPC, running on a Powerbook G4 17. Im able to mount my OS X partition with this terminal command. 

```
sudo mount -t hfsplus -o "ro" /dev/hda3 /media/mac
```

But everytime I log out of Kubuntu and restart my Mac, then boot up kubuntu again the partition isnt mounted, and I have to type in the command everytime. Is there a way for me to automount my os x partition everytime I boot into Kubuntu?

This is my fstab

[IMG]http://i7.tinypic.com/2pzhan9.png[/IMG]

---

### Post by grazie on 2007-02-06
There was a [recent post]("http://www.ubuntuforums.org/showthread.php?t=344963") on how to do this.

---

