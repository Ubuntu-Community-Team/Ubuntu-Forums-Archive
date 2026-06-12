---
title: "how to mount devices in linux"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-09-29
i reformated my NTFS partitions using partiotion magic (yeah i know, it's a sahme i did that in windows) turning them into FAT32 as i wasn't able to write on them. problem is now i can't even "see" them while being in linux. the error message says "couldn't mount image"...well, how do i do that?

---

### Post by Titan_Prometheus on 2006-09-29
So wait, what partitions did you convert to FAT32? All of them? Which One's? I assume it's the device hda2, or 3, etc. what's the command you are trying to run? if it is next in the partition line, you should just be able to run 
sudo mkdir /mount/hda2
sudo mount /dev/hda2 /mount/hda2

---

### Post by Ben Sprinkle on 2006-09-29
Make a new folder on desktop:

cp '/home/user/Desktop/newfolder' '/dev/mnt/'
mount -o 'iso' '/dev/mnt/newfolder'
Might be wrong.

---

### Post by x64Jimbo on 2006-09-29
Ummmm guys, there is a tutorial for this already:
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

---

### Post by Vorticon on 2006-09-30
I still have a question about this, i followed the tutorial to mount 3 windows ntfs partitions.
If i want to acces the first one in nautilus, i have to go to "filesystem" and then to the folder /windows (where i placed it in).
For the other two i made the folder /wingames and /windowns. I see the last two in the "filesystem" but also as a drive/partition next to the "filesystem". Now how do i get the first drive (/windows) to show as a real drive outside the filesystem too instead of as a folder?

Thanks in advance from a complete linux newbie :)

---

### Post by CatKiller on 2006-09-30
> **Vorticon said:**
> I still have a question about this, i followed the tutorial to mount 3 windows ntfs partitions.
If i want to acces the first one in nautilus, i have to go to "filesystem" and then to the folder /windows (where i placed it in).
For the other two i made the folder /wingames and /windowns. I see the last two in the "filesystem" but also as a drive/partition next to the "filesystem". Now how do i get the first drive (/windows) to show as a real drive outside the filesystem too instead of as a folder?

Thanks in advance from a complete linux newbie :)

Put it on a different hard drive :) I'm guessing that that's why you're getting icons in addition to mounting them in the filesystem. Or I could have completely misunderstood what you're saying.

---

### Post by Vorticon on 2006-10-01
Nevermind, they all moved to the filesystem after reboot :)

---

