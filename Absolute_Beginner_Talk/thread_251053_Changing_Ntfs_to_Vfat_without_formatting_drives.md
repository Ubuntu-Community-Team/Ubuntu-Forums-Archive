---
title: "Changing Ntfs to Vfat without formatting drives"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by manojvekaria on 2006-09-04
I got three partitions on my drive. All of them are ntfs. one of them is windows. I can temporarily remove my docs, in the other two drives. 
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
How do i convert my windows ntfs drive to fat32 without uninstalling windows or formatting the drive. I don wana lose my programs and settings. 

I would have a headache coz i got the huge list of programs and settings.

It would be interesting if ubuntu could do this!!!!

---

### Post by dunklegend on 2006-09-04
If your windows is XP it has to be formatted as NTFS but you could reformat any of the other two partitions to FAT32

---

### Post by manojvekaria on 2006-09-04
I don think that would help me.

Can i mount the Xp drive with ubuntu and give it read wirte support with ntfs-3g?

---

### Post by szf on 2006-09-04
>> How do i convert my windows ntfs drive to fat32 without uninstalling windows or formatting the drive.

I don't think that the second part is possible, the first part may be unnecessary - if you're willing to use ntfs support under Linux. Take care with that...

---

### Post by orb9220 on 2006-09-04
"Can i mount the Xp drive with ubuntu and give it read wirte support with ntfs-3g?"
Yes tho it is still considered experimental and may or may not corrupt files.

No you cannot convert a winXp ntfs partition to fat32. 
You can however reinstall xp to a fat32 or you can convert any other ntfs to fat32 with partition magic 8.05 as I did with a 2nd hd that was ntfs. I defrag first then used PM8 to convert to fat32.

But because of the way xp itself behaves you cannot convert the partition that it resides on,

---

