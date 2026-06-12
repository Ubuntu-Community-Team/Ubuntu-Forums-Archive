---
title: "Looking for File-Sharing programs."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Dev0205 on 2007-06-12
Linux Community,

Hi, I'm trying to find a few good file sharing programs to use in Ubuntu. I haven't had much luck with Amule or BittTorrent. Basically looking for one program to do my random mp3 downloads, and another for the larger ISOs and such. I'd appreciate any suggestions.

Thank you,
Dev 0205

---

### Post by jackmc on 2007-06-12
Normally I'd say bittorrent. What is the problem with it?

Only for legal content of course :D

---

### Post by starcraft.man on 2007-06-12
Ktorrent

It handles multiple downloads in the same large window and has many configurable options. I think its the best client I've ever used.

To install open any terminal and paste this in:

Please be sure to enable the backports of Feisty to get the latest version 2.14, it solved the crashing issue in the earlier version.

To enable the repo, go System > Administration > Software Sources > Updates tab at top > Check (an X) in the "Unsupported Feisty (Feisty Backports) line. Then close it and update your sources with the following.

```
sudo apt-get update
```

```
sudo aptitude install ktorrent
```

Enjoy, its in the menu then.

---

### Post by Dev0205 on 2007-06-12
Thank you both! I'll look into those. Any suggestions on something I would use to download single small files? Something like Limewire? I may just be a noob but files I choose to download in Amule never get past 0%.

---

### Post by wh0rd on 2007-06-12
**Transmission**
[http://www.getdeb.net/app.php?name=Transmission](http://www.getdeb.net/app.php?name=Transmission)
-Best torrent manage on linux.

**Nicotine Plus**
[http://www.getdeb.net/app.php?name=Nicotine+Plus](http://www.getdeb.net/app.php?name=Nicotine+Plus)
-Your P2P needs.

And finally Limewire's cousin in Linux: **Frostwire** a Java P2P client via:
```
sudo aptitude install frostwire
```

---

### Post by Dev0205 on 2007-06-12
Exactly what I was looking for! Thanks! :D

---

### Post by Hallvor on 2007-06-14
> **Dev0205 said:**
> Thank you both! I'll look into those. Any suggestions on something I would use to download single small files? Something like Limewire? I may just be a noob but files I choose to download in Amule never get past 0%.

Files in aMule may take a while to download, especially the first chunk. But that is the price you  must pay for files you can`t find anywhere else. Users on aMule share hundreds of files on average and has a very large user base.

For popular files, I`d go for a bittorrent client. aMule for whatever you can`t find on bittorrent.

---

