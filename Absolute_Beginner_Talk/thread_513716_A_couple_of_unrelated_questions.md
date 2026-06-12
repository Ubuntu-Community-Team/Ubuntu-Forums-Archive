---
title: "A couple of unrelated questions"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Shador5529 on 2007-07-30
Question 1:
I am finding DosBox to be running too slow, so I want to make a dual boot Ubuntu/M$-DOS system. (Old School FTW).  My current partition config is:
/dev/hda1 = Primary partition, ext3 file system - this is my /root.
/dev/hda2 = swap partition
/dev/hda3 = extended partition
/dev/hda5 (where's 4?) = logical partition on /dev/hda3 - this is my /home - also ext3 file system

My first question is - what would be the best way to add M$-DOS to this configuration?

----------------------------------------

Question 2
*removed* - Answer given.

Thanks
-Mike

---

### Post by p_quarles on 2007-07-30
On 1, I think you would just need a very small partition and install it to that. I remember using DOS on a machine with a 40 MB hdd, so when I say small, I mean really small. 

What I don't know is whether grub will know how to handle a DOS partition. 

For 2, I believe you could do that, but it would make things more difficult. As I understand it, any command that you want to be able to execute regardless of your working directory needs to be either in /bin or /usr/bin, and not in a directory specifically made for that application.

---

### Post by Warren Watts on 2007-07-30
DOS uses FAT16, so I don't think grub would have a problem recognizing it.

---

### Post by Shador5529 on 2007-07-30
Ok, so - I create a FAT16 - Do I make this a Primary or a Logical? - Can there be multiple primarys?  If not, what do I do with my /root?  And How do I get GRUB to add this to the menu?

Thanks
          -Mike

---

### Post by Shador5529 on 2007-07-31
*bump*

---

### Post by AtrejuT on 2007-07-31
There can be at most 4 primary partitions so you have one more free. (So far hda1-3 are your primary partitions.) This also explains your questions about the missing partition 4: all logical partitions within an extended partition are labeled starting with 5 for exactly this reason.

ps\ please don't remove your old questions, they might still be useful for other people.

---

### Post by Shador5529 on 2007-07-31
So I can remove some space from my /root and make primary 4 as FAT16 then install MS-DOS.  Doubtless, however, MS-DOS will remove GRUB.  How do I fix this problem?

---

### Post by Shador5529 on 2007-07-31
*bump*  (Wow, This is one busy forum)

---

### Post by p_quarles on 2007-07-31
Like editing the partitions, this can be done with the Ubuntu live CD. Here's a guide:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by Shador5529 on 2007-07-31
Well, after all this trouble, created a FAT16 Partition and all, and - surprise, surprise - MS-DOS intaller won't play nice with a Linux formated disk.

I think I'll just wait until I get the Fiesty disk, then wipe, install MS-DOS, and install Fiesty on top of that.

Thanks for all the help though, guys.

---

