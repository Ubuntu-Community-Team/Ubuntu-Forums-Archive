---
title: "Re-starting from 0"
date: 2005-07-04
forum: Absolute Beginner Talk
---

### Post by pat_togo on 2005-07-04
Hi all,
I have tried to install Linux on a system with Windows installed (on D) and have lost it no way to get it back from the boot despite all the advices received already on this forum.
I would like to restart from 0, as far as I know I should re-install Windows first, but what should I pay attention to Ubuntu when re-installing? C is my system partion and it is where I plan to install Ubuntu, should I format it as Ext2 or Ext3 or others? 
Your help would be much appreciated!
Patrick
Shanghai & Lome

---

### Post by knewbix on 2005-07-04
Hello. You can always save what's there but from your question, I'm guessing you hit problems and so I won't go into that. If you are starting from a clean slate, just make three partitions. One NTFS (for Windows) and the others, well, I dunno what is best. Make it reisfers (spelling is probably wrong). For Linux. You should also make the third partition a swap partition AFAIA. Here is an example of what I mean, in case it helps:

1: Windows - NTFS format - Windows
2: Linux - reiserf format - Linux
3: Linux Swap - swap format - Linux swap file, dont worry about it

---

### Post by poofyhairguy on 2005-07-04
[QUOTE=knewbix]Hello. You can always save what's there but from your question, I'm guessing you hit problems and so I won't go into that. If you are starting from a clean slate, just make three partitions. One NTFS (for Windows) and the others, well, I dunno what is best. Make it reisfers (spelling is probably wrong). For Linux. You should also make the third partition a swap partition AFAIA. Here is an example of what I mean, in case it helps:

1: Windows - NTFS format - Windows
2: Linux - reiserf format - Linux
3: Linux Swap - swap format - Linux swap file, dont worry about it[/QUOTE]


Let me correct this a little. 

First: Make two partitions with the xp tool. Leave one unformated, install XP on the other.

Second: Install Ubuntu on the unformated space. You will have to do this in the installer...I don't know how to make it any easier for you. Don't accept the default paritioning set up the installer gives you.

3. The Ubuntu installer will split that second parition into the two the above poster said you need for Linux and will make it so that the dual boot works.

The hardest parts are: making two partitions with the XP install CD (not that hard) and telling the Ubuntu installer NOT to install over your newely made XP install (kinda hard...its wants to erase it by default so you can't just hit yes during the Ubuntu install and have it work).

good luck

---

