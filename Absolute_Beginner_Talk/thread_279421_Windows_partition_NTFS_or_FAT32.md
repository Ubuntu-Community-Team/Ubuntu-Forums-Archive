---
title: "Windows partition: NTFS or FAT32?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Toukejin on 2006-10-17
Ok, I've got a fresh HDD (last one "died"), and I'm going to be installing Ubuntu and WinXP.  Ubuntu will be the primary OS, with Windows only really used for printing, wifi, and anything else I can't get working again in Ubuntu.  

My question: do I format my Windows partition FAT32 and enjoy full access from Linux, or format Windows NTFS and create a smaller FAT32 partition for file sharing.  

The first option would seem like the obvious winner, but I recently read about someone doing the other setup and was wondering if there was some benefit I can't think of.

Thanks again, you guys are always such a big help,
ubern00b Toukejin

---

### Post by oracle5 on 2006-10-17
I have mine set up the second way but mainly because it came with windows installed on it. The only advantage I can think of is that ntfs is better when looking at it from a windows stand point. I've found that xp will run faster on ntfs than on fat32 also but that is just my personal experience, other people may disagree.

---

### Post by Toukejin on 2006-10-17
That's what I've heard, but if I don't really plan on using Windows much, it shouldn't make that big a difference, no?

---

### Post by oracle5 on 2006-10-18
If you aren't going to use it much fat32 would be fine. And I don't have any problem printing under linux, but I do have an Hp printer. I have the same problem as you with wifi though.

---

### Post by lowlymarine on 2006-10-18
I'm going to suggest just using NTFS for the Windows partition, if you're talking about Windows XP (which I assume you are).  XP is faster and more stable on NTFS than on FAT32, and you can actually ahve the best of both worlds here - x86 Ubuntu can mount NTFS partitions with full read/write support.

Try here: [http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS-3g)

Also, if you use Edgy (In Beta right now, but should be finished very, very soon), NTFS-3G is in the repos, so it's as simple as setting your mount points during the install, doing "sudo apt-get install ntfs-3g" froma  terminal window one you're in, and then "sudo gedit /etc/fstab" and changing the type on your ntfs partition from "ntfs" to "ntfs-3g".  Et voila, write support (plus it'll mount with full read support right off the bat, if that's all you need).

---

### Post by Toukejin on 2006-10-18
I had read about 3g, but it scared me a bit.  If it's that easy then I'll give it a go.

---

### Post by theratster on 2006-10-18
I would do the NTFS method. That way you can get the best of both worlds. Install windows on the NTFS partition, but make a FAT32 partition, and then change the My Documents folder to link directly to the FAT32 drive. That way you can be sure to get windows to run fast, and have access to everything you need in Ubuntu.

---

### Post by BLTicklemonster on 2006-10-18
Don't ***** foot around, just make it fat32 and get it over with. Heck, you said you aren't going to use it much anyway. Besides, I have had ntfs and fat32, and I can't blink fast enough to tell a difference.

---

### Post by Toukejin on 2006-10-18
Just set up ntfs-3g and it seems to be working quite nicely.  I'll give that a go for a few days and see if there are any problems.

Thanks again,
Toukejin

---

