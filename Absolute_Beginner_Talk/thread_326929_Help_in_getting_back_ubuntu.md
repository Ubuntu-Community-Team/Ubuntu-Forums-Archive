---
title: "Help in getting back ubuntu"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by abhishekp on 2006-12-28
OK I first installed linux on a primary partition and installed grub on the same partition. It was working well as a double boot system. Now I repartitioned my disk and made one more extra partition to fit in XP and now I can't start linux. Every time I try I get a grub prompt like "grub>" I am not familiar with the commands, but I still tried to edit the menu.lst(with a boot CD) and give all possible numbers for the partition but no luck. I still have all the data on that partition.

Is there any way I can get linux back without any loss of data or settings. And I almost forgot, I have Ubuntu breezy.

---

### Post by deadgobby on 2006-12-28
OK do not listen or feed trolls....
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=grub)
[http://www.ubuntuforums.org/showthread.php?t=88103&highlight=grub+](http://www.ubuntuforums.org/showthread.php?t=88103&highlight=grub+)

Gobby

---

### Post by abhishekp on 2006-12-31
Is there a way to rebuild menu.lst because I checked it and found that it is all messed up. Ithink its because I edited it with dos edit and saved it. And I dont even have the backup of it. thank u

---

### Post by Hossie on 2006-12-31
[Here](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#doc_chap6) is a good explanation how the menu.lst works. Your kernel parameters should be something like:

```
root=/dev/sdaX ro quiet splash locale=aa_BB
```

---

### Post by jerrallan on 2006-12-31
Hi there, I am kind of a newbie but I think you have to put the Windows OS in first.  Then create a partition for Linux. I had similar problems.  You may be okay now if you reinstall Ubuntu.

Jerry

---

### Post by abhishekp on 2006-12-31
thank you jerrallan but I dont want to reinstall I just want to recreate menu.lst so that i will be able to boot into ubuntu.

---

