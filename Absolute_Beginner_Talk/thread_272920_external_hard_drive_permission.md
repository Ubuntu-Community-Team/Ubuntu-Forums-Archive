---
title: "external hard drive permission"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by tospig on 2006-10-07
Hi,

I'm trying to write files to an external hard drive (usb), but it's saying I don't have the correct permissions to do this, does anyone have an idiots guide on how to set correct permissions for this?

I've searched on this site and found a similar topic, but it's too complicated for me to understand :p

---

### Post by unisol on 2006-10-07
im far from an expert but try this go to system-preferences-usersand groups and click on  your account name select permissions and see if it has a permission to write to usb drive if it does check the box youre in business

---

### Post by Kateikyoushi on 2006-10-07
What is the filesystem on that drive ?

---

### Post by tospig on 2006-10-07
Unisol:

The box was checked that says I can access external drives, but nothing about permissions and writing to it.

Kateikyoushi:

I don't know - a friend of mine has lent it to me. Does it make a difference as to what the filesystem is?

Is there a way I can find out? (I won't be able to speak to him for a couple of days.)

---

### Post by Kateikyoushi on 2006-10-07
It is important because by default you can not write to NTFS partitions which  would explain your problem.

The next command will list the hdds and the partitions in your machine.
```
sudo fdisk -l
```

---

### Post by tospig on 2006-10-07
oh, it says:

system
HPFS/NTFS

---

### Post by zappa on 2006-10-07
Since it is your friend's and I also suppose it's NTFS, I would only read, not write onto it. The best option to share between Win and Lin is still a FAT32 ;)

---

### Post by tospig on 2006-10-07
but is there a way i can write to it, as this is what I want to do?

---

### Post by Kateikyoushi on 2006-10-07
If it is a must you can try [this]("http://ubuntuforums.org/showthread.php?t=217009") or reformat the drive to fat 32, after backing it up.
Of course ask your friend first.

---

### Post by tospig on 2006-10-07
ok, seems a bit complicated for me - I think I'll just format it to FAT32, thanks for you help :)

---

### Post by TheGrinch on 2006-11-17
tospig, I had the same problem until I installed Xandros Home Edition-Premium (you can register for a trial version) on another PC & connected the external hard drive. Xandros has the built in ability to write to NTFS partitions. To my surprise when I connected the external hard drive to my Windows XP PC & created a share for it, I could then connect to the share from my Ubuntu PC & write to the hard drive

---

