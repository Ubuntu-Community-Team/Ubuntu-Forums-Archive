---
title: "Changing drive\directory permissions"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Vlammend on 2005-11-26
Hello All,

With Hoary and with Breezy I have th following problem:
During installation I create one FAT32 drive to exchange files with Windows XP or to store files I am using under Windows and under Ubuntu. The drive is hooked up under \LinWin
After installation, the owner of the drive (directory) is root. Every other user has read and executing rights, but I want write rights too.
With sudo I can not get it done:
```
sudo chown hildebrand /LinWin/

```
gives: > chown: changing ownership of `/LinWin/': Bewerking niet toegestaan
 Which means, change not allowed.

```
sudo chmod o=rxw /LinWin/

``` Does not give any feedback, but it does not change the rights either!!!

How can I solve this?:confused:

---

### Post by akiro.yamamoto on 2005-11-26
I got this info from an old linux set-up guide....
Lets Assume that your FAT32 partition is /dev/hda2 (2nd partition 1st / primary drive)
 CODE
sudo umount /dev/hda2
sudo rmdir /media/Lin4Win
sudo mkdir /media/Lin4Win
sudo cp /etc/fstab /etc/fstab.back
sudo gedit /etc/fstab

When Gedit opens up, find any reference to /dev/hda2 and modify that line to look like this:
/dev/hda2       /media/Lin4Win  vfat    iocharset=utf8,umask=000      0        0

This should solve the problem..

I found this reference site that should help you out...

URL: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)
Author: Chua Wen Kiat (Kuala Lumpur, Malaysia)

It's for 5.04 but it should give you a leg up. :smile:

---

### Post by Vlammend on 2005-11-26
From the reference site I added (after the fstab change)
sudo mount -a

and then the permissions seem to be ok.

Thanks for the help

---

