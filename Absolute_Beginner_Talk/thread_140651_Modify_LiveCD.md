---
title: "Modify LiveCD?"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by ctkennedy on 2006-03-06
Hello,

I have been palying with the liveCD version 4 of Dapper and love it.  Very stabble.  I am  a high school teacher and want to help students make their own live versions using this is the base ISO.  How would I go about helping them create their own customized liveCD?  One that hopefully can be installed as well!??

Thanks in advance,
Clint Kennedy

---

### Post by Brunellus on 2006-03-06
[QUOTE=ctkennedy]Hello,

I have been palying with the liveCD version 4 of Dapper and love it.  Very stabble.  I am  a high school teacher and want to help students make their own live versions using this is the base ISO.  How would I go about helping them create their own customized liveCD?  One that hopefully can be installed as well!??

Thanks in advance,
Clint Kennedy[/QUOTE]
That's a pretty tall order.  Don't know about Dapper Flight 4, but there is a page on the wiki about LiveCD customization:

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28livecd%29](https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28livecd%29)

---

### Post by luopio on 2006-05-06
Wiki works if you're customizing hoary or breezy, but in dapper you have the squashfs instead of cloop. Basically you can follow the instructions in the wiki and change a few commands. 

Here are the commands that need changing (just replace the corresponding ones in the wiki with these): 

Installing tools:
```
apt-get install squashfs-tools mkisofs
```

copying the iso-image contents excluding the filesystem: 
```
rsync --exclude=/casper/filesystem.squashfs -a mnt/ extracted_cd
```

extracting the squashfs contents so that they end up RW in "mnt" (the same state as in the wiki after the operations):
```
mkdir extracted_fs
mkdir squashfs

sudo mount -o loop -t squashfs mnt/casper/filesystem.squashfs squashfs

sudo cp -a squashfs/* extracted_fs/
sudo umount squashfs/
sudo umount mnt/

rmdir mnt/
mv extracted_fs mnt
```

creating the squashfs-image after the "cleaning" operations:
```
sudo mksquashfs mnt.new/ extracted_cd/casper/filesystem.squashfs
```

That should be all.. sorry if I didn't cover em all. :?

---

