---
title: "Help!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by kraddark on 2008-02-09
I followed the procedure on how to make my 2GB USB drive an UBUNTU installer but the problem is i can restore it to its original size.. i can only see 716 MB / 2GB.. how can restore it back? please help me..

---

### Post by Rocket2DMn on 2008-02-09
If you are finished using the drive for that purpose, you can download GParted to use to reformat the drive.
```
sudo apt-get install gparted
```
Then plug in the drive and go to System->Administration->Partition Editor
Choose your USB drive (/dev/sdb perhaps) from the top right where is says /dev/sda (or something similar) and tell it to reformat it with FAT32.  You may need to delete the existing partition first.
Make sure you're selecting your flash drive!
If it complains about it being mounted, you need to unmount it first by right clicking the desktop icon.

---

### Post by nikoPSK on 2008-02-09
> **Rocket2DMn said:**
> If you are finished using the drive for that purpose, you can download GParted to use to reformat the drive.
```
sudo apt-get install gparted
```Then plug in the drive and go to System->Administration->Partition Editor
Choose your USB drive (/dev/sdb perhaps) from the top right where is says /dev/sda (or something similar) and tell it to reformat it with FAT32.
Make sure you're selecting your flash drive!
If it complains about it being mounted, you need to unmount it first by right clicking the desktop icon.

you could do ntfs as well if you wanted, choice is yours (whatever fits your needs. )

---

### Post by kraddark on 2008-02-09
> **nikoPSK said:**
> you could do ntfs as well if you wanted, choice is yours (whatever fits your needs. )

do you have anay idea on how i can do this under windows xp?

---

### Post by nikoPSK on 2008-02-09
> **kraddark said:**
> do you have anay idea on how i can do this under windows xp?

don't listen to me :lol:! Well, in gparted, just format is as ntfs (but fat 16 is better)

---

### Post by Rocket2DMn on 2008-02-09
Say in windows it shows up as drive f:\
Open a command prompt (Start->Run and type in "cmd" without quotes).  The run
```
format f: /FS:FAT32
```

---

### Post by nikoPSK on 2008-02-09
> **Rocket2DMn said:**
> Say in windows it shows up as drive f:\
Open a command prompt (Start->Run and type in "cmd" without quotes).  The run
```
format f: /FS:FAT32
```

well, in windows... sure. :lol:

---

### Post by barbedsaber on 2008-02-09
sorry to jump into the middle of a conversation, but can I please ask that you make a real effort to make the title to your threads as usefull as possible, perhaps something like need help making USB drive ubuntu installer would have been more helpful. thanks anyway, and I hope you get your problem fixed.

---

### Post by nikoPSK on 2008-02-09
> **barbedsaber said:**
> sorry to jump into the middle of a conversation, but can I please ask that you make a real effort to make the title to your threads as usefull as possible, perhaps something like need help making USB drive ubuntu installer would have been more helpful. thanks anyway, and I hope you get your problem fixed.

+1

---

