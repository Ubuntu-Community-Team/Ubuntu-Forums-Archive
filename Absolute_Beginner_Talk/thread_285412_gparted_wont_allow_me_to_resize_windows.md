---
title: "gparted wont allow me to resize windows"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by Space Cowboy on 2006-10-26
I am not sure whether this should go here or in support but to me it sounds like a really basic question. A month ago I got a gateway laptop (an mx6920). Like all gateways instead of a windows install disk it came with a recovery partition. When I first installed ubuntu I made a 25gb partition for it, installed it and it has worked fine, I have had no problems with it and I am learning alot (these forums are really helpful :D ). I have found a way to substitute almost anything I can do with windows in linux but I do still need windows for certain things.

So my problem is I want to resize my windows partition to have more space for linux or a fat32 data drive, but when I run gparted it will not let me resize it. I have done everything I need to, I defragged windows, ran a chkdsk, ran gparted with root and unmounted the windows partition but it still will not let me resize it. Someone has mentioned to me they didnt think it was possible to resize if your drive isnt [Windows | Linux | Swap] (mine is [recovery | windows | linux | swap]) but I dont know how trustworthy that person is...

I need to keep the recovery partition because windows has already went screwy on me once and I had to reinstall it, which will be impossible in the future if I remove it. I also do not want to reinstall ubuntu because I am on dialup (I live in a rural area) and I have installed a ton of updates and programs, which I wouldnt want to go to waste...

Any help on the matter is appreciated.

---

### Post by Rackerz on 2006-10-26
I don't think gparted will resize it, as it's NTFS.

---

### Post by Space Cowboy on 2006-10-26
Well I know I resized the windows partition when I first installed Ubuntu and it was still NTFS, so I assume there is a way to do this, if not with gparted then how?

---

### Post by Sef on 2006-10-26
> I don't think gparted will resize it, as it's NTFS.

I have used it resize NTFS.  [Resizing NTFS]("http://gparted.sourceforge.net/features.php")

> So my problem is I want to resize my windows partition to have more space for linux or a fat32 data drive, but when I run gparted it will not let me resize it.

Do you have the current version of [GParted]("http://gparted.sourceforge.net/")? If not, then download it.

---

### Post by Rackerz on 2006-10-26
[QUOTE=Sef;1669103]I have used it resize NTFS.  [Resizing NTFS]("http://gparted.sourceforge.net/features.php")

Pardon me then. I must have been thinking of the livecd.

---

### Post by CupofDice on 2006-10-27
```
sudo apt-get install ntfsprogs
```
That worked for me.

---

