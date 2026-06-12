---
title: "WinXP vs Linux space"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by cburg on 2005-09-23
I am very new to Linux and lack confidence to do much.  I have WinXP (FAT32) on my first HD (20 GB) and Ubuntu 5.04 on the second HD (13 GB).  It dual boots using grub with no problems.  Windows doesn't recognize the second HD anymore so does that mean it is all "reserved" for Linux?  Is there an easy way for me to tell how much space is left on the Linux HD?  If there is enough space left, can I give some of it back to Windows, and if so, how?

I have backed up my Windows files but I still don't want to lose anything if possible and I would really like to do something easy and successful to help build my confidence.

Thanks in advance - dale

---

### Post by xequence on 2005-09-23
Windows cant see linux drives as far as I know, without a certain program. A link is on ubuntuguide.org :)

---

### Post by wishyjr on 2005-09-23
alright mate, im another beginner here so i know exactly how you feel! :)

as for your question, you're sayin you've got two physical hard drives? one 20GB and the other 13GB? if so the reason windows cant see the 13Gb (linux) drive is because its formatted as ext3 and not FAT32 or NTFS which is what windows uses. Linux needs to be installed onto a ext3 formatted drive. 

you should be able to partition some of the 13GB drive and format the new partition into FAT32 or something so windows can read it.... i think... :) just waitin for someone to tell me ive got it all worng now lol!!

---

### Post by xequence on 2005-09-23
What I do is have one fat32 partition for my music and stuff both windows and linux can see and write to.

---

