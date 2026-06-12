---
title: "32 bit 5.04...what a difference!"
date: 2005-06-30
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-30
Wow! What an immediate difference the 32bit version of 5.04 is over 4.10 64bit! I was only using the former for two days and it's obvious!

Question...I have two partitions. One is 100gb primary and other is 150gb logical. When I created the logical it automatically called itself /home - however in places/computer I only see one drive called "filesystem" as well as my optical drive. I don't understand how linux handles partitions so how do I check if my home directory is actually on the 150gb partition?

Also doing properties on filesystem fails to give me a total size :( and my dvd-rw drive claims to have 87.5gb free space. Quite impressive I am sure you will admit!...right...gotta get dual screen running...is it possible without installing ATI drivers?

EDIT: I am really over the moon now! My iAudio M3 works fine under 5.04 32bit when it could not be read under 4.10 64bit. So happy! Windows does nothing I need practically any more.

---

### Post by akcanadianeh on 2005-06-30
Filesystem is not a drive in and of itself in Linux. It is every file on your computer, anywhere. According to your post, /home will be your logical drive, the rest of the filesystems will be on your primary (with the exception of /dev, which is actually in memory and not stored on a drive at all i believe... correct me if I'm wrong on this). Even the optical drive is actually in filesystem (probably somewhere in the /media directory. This is very different than how, say, windows conceptualises your computer. If you browse your filesystem, the free space listed on the bottom of the window will change as you browse in filesystem onto different drives. For example in / (the root) free space will be for your primary, but change to /home and the free space will change to reflect the logical.

---

### Post by gammyhand on 2005-06-30
[QUOTE=akcanadianeh]Filesystem is not a drive in and of itself in Linux. It is every file on your computer, anywhere. According to your post, /home will be your logical drive, the rest of the filesystems will be on your primary (with the exception of /dev, which is actually in memory and not stored on a drive at all i believe... correct me if I'm wrong on this). Even the optical drive is actually in filesystem (probably somewhere in the /media directory. This is very different than how, say, windows conceptualises your computer. If you browse your filesystem, the free space listed on the bottom of the window will change as you browse in filesystem onto different drives. For example in / (the root) free space will be for your primary, but change to /home and the free space will change to reflect the logical.[/QUOTE]
 Thanks. I think I understand it now. It's so much better than windows system. Just a lot to get used to. I have been winstitutionalised :(

---

### Post by poofyhairguy on 2005-06-30
Well...your patience paid off gammyhand. I hope this forum has given you the service you needed.

[QUOTE=gammyhand]Quite impressive I am sure you will admit!...right...gotta get dual screen running...is it possible without installing ATI drivers?
[/QUOTE]

No...not really.

---

