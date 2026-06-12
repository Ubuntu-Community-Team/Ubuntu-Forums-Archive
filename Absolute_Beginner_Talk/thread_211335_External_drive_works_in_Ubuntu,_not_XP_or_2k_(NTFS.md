---
title: "External drive works in Ubuntu, not XP or 2k (NTFS)"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by CK05 on 2006-07-08
Okay I'm stuck here. Basically my external hard drive doesn't work at all on two XP machines and a win2k machine but works perfectly fine when I boot with my Ubuntu live CD. 

What can I do? I need my data so I'm thinking of:

- Booting into Ubuntu (LiveCD)
- Transferring my data onto my local hardrive (I only have one)
- Then formatting my external HDD. 

The problem is how the hell do I go about this? 

Ubuntu won't mount my Windows C: drive. Any help is appreciated because I have a lot of important portfolio files on that drive :(.

Cheers!

---

### Post by someusernoob on 2006-07-08
Need to know a couple of things:

1. What file system does tour external HDD use?
2. What file system do the Windows installations use?

If your Windows installations are all NTFS and you do not have extra partitions or free space to create partitions youre in trouble. Linux can not write to NTFS. There is a way if you search for it, but i wouldnt recommend that, since its not safe!

If you have free space/partitions on your hard disk (not the external) format them to FAT32, Linux can write to those without a problem. so then you'll be able to backup the stuff from the external HDD.

Otherwise i would recommend to burn the data you want to keep to a cd or dvd.

---

### Post by mit on 2006-07-08
Spinrite might be able to repair your drive/recover your data. Availible from [http://www.grc.com]("http://www.grc.com")

---

### Post by CK05 on 2006-07-08
Sweet, thanks for the replies.

Both Windows and the external drive are in NTFS. I might give the FAT32 option a go but I have never partitioned a disk before. Way too much data to put to CD though!

I'll also give spinrite a go but I have tried to use other drive recovery programs but none of them have worked. I'm aware of grc.com though so I'll try 

 have to go to work now but I'll try your suggestions later. 

Thanks for the fast replies! :cool:

---

