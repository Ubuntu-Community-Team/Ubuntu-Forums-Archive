---
title: "Quick question about using an NTFS drive as a backup."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by DragonKore on 2007-12-04
I recently migrated from Windows, and on Windows I was using an 80GB drive as a backup for my music, videos, pictures, etc. I can see the drive in Ubuntu, I can access the files, I can do everything I need to. My question is whether or not there are any negative side effects to using an NTFS drive as a backup.

I'm not a file system guru, so I don't know if it's slower than ext/ext3. If you guys recommend that I convert it to ext, how would I do that without losing all of my files?

Thanks for the help.

(I hope this hasn't been asked dozens of times before. I did a search but found nothing pertinent.)

---

### Post by StitchJAcket on 2007-12-04
As far as backup goes. Using NTFS is a great idea because you can easily pull files from it with alot of different operating systems. In reality the whole point to having a backup drive is so that in the event that your operating system fails you have a backup of all your files. Obviously using something like FAT 32 might be better but for you there really is no disadvantage to NTFS =)

Hope that helps?

---

### Post by DragonKore on 2007-12-04
Perfect, that's all I wanted to know. Thanks for the answer, mate.

---

### Post by StitchJAcket on 2007-12-04
> **DragonKore said:**
> Perfect, that's all I wanted to know. Thanks for the answer, mate.
Anytime ;)

---

### Post by timcredible on 2007-12-04
ntfs write is not good in linux - use fat32 if you need to use it on both OSs.  beware that fat32 doesn't support file permissions though, so taring the info first would be best with a fat32 partition.

---

### Post by StitchJAcket on 2007-12-04
> **timcredible said:**
> ntfs write is not good in linux - use fat32 if you need to use it on both OSs.  beware that fat32 doesn't support file permissions though, so taring the info first would be best with a fat32 partition.
I use an NTFS drive as my backup and it actually writes better in linux than it does in windows for me. However if your comparing it to ext2 or 3 then yes you wont get those fast or write speeds. Another option is to use the ext 2 filesystem and if u use windows use a program called IFS which will recognize those filesystems and allow you to mount and use them in windows ;)

---

