---
title: "installing winxp after osx and ubuntu"
date: 2009-09-20
forum: Apple Hardware Users
---

### Post by rifak on 2009-09-20
hey everyone,
i already have osx and ubuntu 8.04 installed and working on my macbook3,1 (santa rosa) and now i want to try to put winxp on it. i already made a partition for xp so i have an osx, ubuntu, linux swap, and an ntfs partition (the ntfs doesn't have anything on it yet). however, when i put in the xp installation cd and choose that partition, it says that it can't make another partition due to already having too many. so, i tried deleting my linux swap and it still gave the same error. i am wondering if there is any way around this without having to delete and reinstall ubuntu.

---

### Post by Bachstelze on 2009-09-20
If you created a partition for XP, you shouldn't need to create one during installation. Just format the one you have already created.

---

### Post by Bucky Ball on 2009-09-20
Can you post the results of:

```
sudo blkid
```

---

### Post by rifak on 2009-09-20
yea that's exactly what i thought too. but when i used gparted i tried formatting in both fat32 and ntfs and neither of that worked. it still said that it couldn't proceed with the installation.

---

### Post by rifak on 2009-09-20
resuls of sudo blkid:

```
/dev/sda1: LABEL="EFI" UUID="3F3C-1AF6" TYPE="vfat" 
/dev/sda2: TYPE="hfsplus" 
/dev/sda3: UUID="aaf6578b-cd77-43df-ac15-cc6effdcd885" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="23361f1c-dc02-496b-b9b2-b104391cbfd7" 

```

---

### Post by Bucky Ball on 2009-09-20
Yep, four is it. You need to have an extended partition and put your logical drives/partitions in that if you want more.

You can have four partitions (per physical disk) but ***inside ***an extended partition you can have lots.

---

### Post by rifak on 2009-09-20
any tutorials or docs you can point me to on how to do that?

---

### Post by Bucky Ball on 2009-09-20
Well, no matter how you go about it, it will involve either another physical hard drive or making some space on the one you have, creating an extended partition and putting what you have in there.

There is a catch. Windows XP will *not *work as a logical drive in an extended partition. *Must *be a primary partition and preferably first up (although this last part is not essential just easier to get XP up).

Are there any installs you have recently done and are not too attached to? Can you backup your personal data? If so there should be some way around it. I don't know if osX also needs to be on a primary partition but these are thing you should consider. Ubuntu does not and will happily run inside and extended partition.

---

### Post by rifak on 2009-09-20
alright, thanks for your help. it's not worth it. the only reason really is because i'm bored and have nothing to do today and figured i would mess around with it but it's definitely not worth it (especially because i'll never use it). i appreciate the help though.

---

### Post by Bucky Ball on 2009-09-20
Could you mark as solved from 'thread tools'? :)

---

