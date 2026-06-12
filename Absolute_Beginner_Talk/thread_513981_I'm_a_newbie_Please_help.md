---
title: "I'm a newbie: Please help"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by godling on 2007-07-31
[FONT="Verdana"]Since forum conversations tend to deviate a lot, I'll keep it simple:

I'm totally new to Ubuntu, and have the following questions:

01. Does Ubuntu have a live-on-cd version, like Knoppix?

02. If it does, then will the live version recognize an NTFS formatted portable Harddisk drive if I plug the same into my USB port?

03. If not, is there a way I can get it done?

Basically I have a portable HDD, formatted in NTFS. Someone told me
Knoppix live-on-cd cannot access that.

Can Ubuntu access that?

Thanks. Waiting for your responses.[/FONT]

---

### Post by Spr0k3t on 2007-07-31
All of the *buntu ISO images are live discs and can be loaded as such.  I have an NTFS formatted USB drive that I just tested with a Feisty LiveCD and it did work... however it is read only.  You may want to give Knoppix a shot just in case as ntfs-3g is supported... I just can't remember if it will read USB ntfs or not.

Edit: One exception to the rule... the Alternate Install discs are not Live discs.

---

### Post by wormser on 2007-07-31
> **godling said:**
> [FONT="Verdana"]
01. Does Ubuntu have a live-on-cd version, like Knoppix?

02. If it does, then will the live version recognize an NTFS formatted portable Harddisk drive if I plug the same into my USB port?

03. If not, is there a way I can get it done?

Basically I have a portable HDD, formatted in NTFS. Someone told me
Knoppix live-on-cd cannot access that.

Can Ubuntu access that?[/FONT]

1.  The Ubuntu install CD is also a live CD
 
2.  No/Yes

3.  The live CD will recognize the NTFS hard disk but you will not be able to write with out the NTFS-3G package installed.  It can be done but you would have to install the NTFS-3G package and create a new live CD.  Somebody else will have to help you with that because I have not done it.  Why just not create a new partition and install Ubuntu as a dual boot?

---

### Post by hyper_ch on 2007-07-31
Not all of them are live cds :) just the Desktop versions ;)

---

### Post by tomcheng76 on 2007-07-31
Desktop Version are LiveCD and able to provide NTFS read services
if u have internet connection on that PC that u are gonna to insert the livecd into
you can try type this when u have network and running the LiveCD
```

sudo apt-get install ntfs-3g
sudo umount /dev/<your removable drive>
sudo mkdir /media/temp
sudo mount -t ntfs-3g -o defaults,locale=en_US.utf8,umask=000 /dev/<your removable drive> /media/temp

```
then you can read write your portable Harddisk drive , as ntfs-3g is temporary installed on the memory cache

if you dont have a internet connection and you want to add ntfs write support
u can try to remaster the Desktop CD
search Ubuntu Linux remaster on Google

---

### Post by godling on 2007-07-31
Ok, so Ubuntu can ONLY READ from NTFS without any extra installs, I've got that.

Is it the same for FAT32 as well? I can format my portable HDD to have the FAT32 filesystem.

Will Ubuntu to able to WRITE TO FAT32, or do we need some thing more to be installed for
that to happen?

Thanks.

---

### Post by hyper_ch on 2007-07-31
Ubuntu fully supports Fat32 read and write... however fat32 is an ancient system... it has no journaling and cannot hold files larger than 2gb...

---

### Post by godling on 2007-07-31
That's really not my concern, and I'm not dealing with quota management, IDX
indexing or other facilities like encryption and data compression.

My principle requirement is to move data, into a portable USB HDD, using a live
version of Ubuntu.

FAT32 fits that bill like second skin.

Thanks so much for all your answers. I can see this is one community which
moves really fast. Glad I landed up here.

---

### Post by ashokcm on 2007-07-31
You should be careful using FAT32 for moving your data. Especially if it is very important data. I would recommend a backup on DVDs or CDs (just in case). I recently lost a lot of data trying to do that with FAT32. It seems FAT32 has a problem with reliability when it comes to improper ejects. Apparently ubuntu edgy had a bug which caused incomplete ejection of the USB drive. That corrupted my drive and all data in it.

---

### Post by qamelian on 2007-07-31
> **hyper_ch said:**
> Ubuntu fully supports Fat32 read and write... however fat32 is an ancient system... it has no journaling and cannot hold files larger than 2gb...

The file size limit on FAT32 is 4GB, not 2.

---

### Post by hyper_ch on 2007-07-31
it's 4GB? Well, anyway much too low ;)

---

