---
title: "Partitioning disc"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by pookz on 2007-05-12
Im a complete newb when it comes to Ubuntu. I just installed it yesterday and completly wiped out my Vista but I want to partition the disc now and have vista on here as well. SO i downloaded gparted but its not letting me partition the disc. Can someone please tell me how i can partition my disc and add vista? any help is much appreciated.

---

### Post by oilchangeguy on 2007-05-12
your best bet is to install windows first. then install ubuntu and set your partitions then.

---

### Post by LE CHARBON on 2007-05-12
Do vista first then do ubuntu second and the live cd will guide you. Careful not to erase vista.

---

### Post by pookz on 2007-05-12
I tried that. It tells me it has to be on an NFTS and I only have ubuntu installed =[

---

### Post by pookz on 2007-05-12
I did erase vista. Can i save it?

---

### Post by LE CHARBON on 2007-05-12
Did you reinstall vista?

---

### Post by pookz on 2007-05-12
It wont let me. It tells me it has to be installed on an nfts harddrive and when ubuntu installed, it went to a different type.

---

### Post by jiminycricket on 2007-05-12
You have to delete that partition first.

After you install Vista, resize the disk for room for Ubuntu in Vista, then install Ubuntu in that spac.e

---

### Post by LE CHARBON on 2007-05-12
I think he wants to do a complete erase and start over. ANYONE?

---

### Post by pookz on 2007-05-12
so put in the install disk for vista. delete this partition? you mean, not formatting it? and it will let me install vista?

---

### Post by pookz on 2007-05-12
i just want vista back so i can make dual booting. and for right now its telling me i cant put vista back on this partition because its not nfts. 

*she

---

### Post by LE CHARBON on 2007-05-12
If vista is asking to reformat the entire disk , I would. then install ubuntu again.

---

### Post by pookz on 2007-05-12
ok so lemme make sure i have this before i go and delete my whole thing. im putting in vista install disk.. going to custom and deleting the harddrive. then installing vista? then later ill worry about ubuntu

---

### Post by LE CHARBON on 2007-05-12
Should be it. then:

This was told to me when i had xandros on. Should help you out.

So, when you get to the partitioner in the live or alternate installer its simple. First, say you want to manually edit the partition table. Next an NTFS partition should be at the top of your list. You want to leave that alone, that should be your xp. I assume that Xandros should be listed right underneath. So if you wanna remove it just select it and delete the partition. Then you want to create 3 partitions. To create just select the free space and push enter, then you'll choose how much drive to give it. Below is how your partitioner should look, tried to make it understandable. Your Ubuntu Root parition should be primary to be booted from and you should enable the bootable flag on it. Swap and Home should be logical, their just data.

Partition List:
- XP Partition, NTFS, X GB, mount /media/hdsomething (can change)

- Ubuntu Partition, Ext3, 6-8 GB, mount /

- Swap File, Swap, 2-3 GB, doesn't mount like drives

- Home partition, Ext3, rest of your drive GB, mount /home

The / is your root directory and you mount your home seperate so that you can keep your data if you reformat your version of Ubuntu.

After your done setting it up, grub will detect your XP install unless its corrupted.

---

