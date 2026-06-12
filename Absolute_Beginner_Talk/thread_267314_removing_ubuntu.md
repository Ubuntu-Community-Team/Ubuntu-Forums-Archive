---
title: "removing ubuntu"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by adidaskid810 on 2006-09-28
i have a lot of info on my xp system and i want to completely rid ubuntu. but will putting the xp install cd completely crash my system and return it to the first day i loaded it? or what is the easiest way to rid of ubuntu...thanks!

---

### Post by adidaskid810 on 2006-09-28
i have a lot of info on my xp system and i want to completely rid ubuntu. but will putting the xp install cd completely crash my system and return it to the first day i loaded it? or what is the easiest way to rid of ubuntu...thanks! i searched but didnt find an answer

---

### Post by pay on 2006-09-28
You can wipe a parition in Windows using Start --> Control Panel --> Administrative Tools --> computer Management --> Disk Management
Then you can delete the paritions you don't want (Right click Delete logical drive) and format a new parition. Then put in you windows cd and boot into the recovery console. Type fixboot and fixmbr (or maybe fix boot, fix mbr i can't remember) to get rid of grub.

---

### Post by hellmet on 2006-09-28
post one more thread and u mite be removed from here:mrgreen:
kidding...
Well, its bad u want to leave Ubuntu for Windows,
but here is ur answer..
if u install XP, then make sure u do it on the first
partition of ur HDD..
second, installing XP will remove Linux GRUB , and u'll
not be able to boot into Linux no more..
now from Win u shud be able to free that Linux partition..
Your system won't crash..

---

### Post by divague on 2006-09-28
To remove ubuntu first you have to remove GRUB, boot from your win cd, when it finish loading select the "r" option, i think is the recovery console or simehting like that, put "fixmbr" without quotes, and reboot your system, that will remove grub, to remove ubuntu, just use a partition program to format the partition where ubuntu is

---

### Post by pay on 2006-09-28
You can wipe a parition in Windows using Start --> Control Panel --> Administrative Tools --> computer Management --> Disk Management
Then you can delete the paritions you don't want (Right click Delete logical drive) and format a new parition. Then put in you windows cd and boot into the recovery console. Type fixboot and fixmbr (or maybe fix boot, fix mbr i can't remember) to get rid of grub.

---

### Post by Eddie Wilson on 2006-09-28
Insert the XP cd and boot. The cd will search and then ask you if you want to install or repair using the recovery console. Using the recovery console type fixmbr (If I remember correctly) and then you will be booting into Xp. Then you will need a partion manager to remove the linux partions.

---

### Post by gn2 on 2006-09-28
To remove Ubuntu simply delete or format the Ubuntu partitions.
This will leave your XP installation intact.

You don't need to remove Grub.
If you do remove Grub, you will need to use the XP disc recovery mode and run "fixmbr"

Removing partitions can be done with a partition editor, for example Partition Magic if you want to spend some money on an excellent product. 

Or you could just download a free one: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Good luck.

---

### Post by Brunellus on 2006-09-28
threads merged.  Please do not post duplicate threads.

---

### Post by sailor2001 on 2006-09-28
in XP, right click "my computer"/ manage/hard drives/partitions and right click on the large "unnamed" partition and delete

---

