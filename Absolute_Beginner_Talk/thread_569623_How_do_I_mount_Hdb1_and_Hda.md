---
title: "How do I mount Hdb1 and Hda???"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Ganda_Melga on 2007-10-07
This is such a basic question  that I must admit I'm a bit ashamed of asking.

Anyway...

How do I mount the other hard drives in Xubuntu??? Knoppix, puppy, slax, they all have an easy way of monting the drives, but not xubuntu.

Xubuntu is in Hdd, Windows 2000 on Hda (Ntfs), and Puppy in hdb1.
When I try to mount a drive this is the result:

melga@retrotech:~$ mount /dev/hdb1
mount: não foi possível localizar /dev/hdb1 em /etc/fstab ou /etc/mtab
melga@retrotech:~$ 

Errr... wich means with wasn't possible to locate /dev/hdb1 in /etc/fstab or  /etc/mtab.

I really like Xubuntu, mas why must it be so difficult to perform such basic tasks???

Any help will be welcome. Thank you.

---

### Post by Pumalite on 2007-10-07
You have to create amounting point first:
sudo mkdir /media/new
sudo mount -t ext3 /dev/sdb1 /media/new
(ext3 could be replaced by ntfs if that is the case)

---

### Post by Ganda_Melga on 2007-10-07
> **Pumalite said:**
> You have to create amounting point first:
sudo mkdir /media/new
sudo mount -t ext3 /dev/sdb1 /media/new
(ext3 could be replaced by ntfs if that is the case)

Hum....didn't worked at first but I managed do make it work just replacing /dev/sdb1 by /dev/hdb1. Thanks a lot for your fast reply.

Now I'm gonna try with the windows 2000 HD.

---

### Post by Pumalite on 2007-10-07
You are welcome. Good luck.

---

### Post by Ganda_Melga on 2007-10-07
Hum.....It seems to mount the windows disk, but I can't see any of it's contents. Puzzling.

---

### Post by Pumalite on 2007-10-07
Did you get a 'lost+found' thing?

---

### Post by Ganda_Melga on 2007-10-07
> **Pumalite said:**
> Did you get a 'lost+found' thing?

There is such a folder on the xubuntu HD, but it's empty. The folder /media/windows is also empty. In the properties it shows the correct free space in the windows disk, but there is this message: 

Falha na leitura do conteúdo da pasta

Wich means it failed to read the contents of the folder.

Any ideias?

---

### Post by Pumalite on 2007-10-07
What format uses that drive?

---

### Post by Ganda_Melga on 2007-10-07
> **Pumalite said:**
> What format uses that drive?


Errr....It's a 10 giga IDE disk (ata), with no partitions, formated to NTFS, and have the windows 2000 installed.

---

### Post by Pumalite on 2007-10-07
You should be able to see and read from ntfs in Ubuntu, so, maybe the drive is mounted somewhere else. Look around or check connections, cables,etc. Make sure is recognized in BIOS

---

### Post by bodhi.zazen on 2007-10-07
To list your partitions use :

```
sudo fdisk -l
```

To see what is mounted where use

```
mount
```

If you could post the outputs of those commands and tell us what partition you want to mount it would be easier for us to help.

---

