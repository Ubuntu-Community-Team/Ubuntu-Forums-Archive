---
title: "Missing Harddrive space?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by linkhows on 2007-07-25
I portioned Ubuntu  to 30.3 gb ( windows xp to 30.2 gb)but in the system monitor it says that I only have 25.4 gb of space and 21.1 gb available. I just installed Ubuntu yesterday and have only preformed an update. I'm wondering where all my hard drive space went and where i could monitor how much space the programs on my computer take up like in windows xp in add or remove programs.

---

### Post by benx009 on 2007-07-25
"sudo apt-get clean" should free up some disk space

---

### Post by Malta paul on 2007-07-25
Try: Sudo fdisk -l   To check your HD partions
Good Luck:)

---

### Post by linkhows on 2007-07-25
Where to I get sudo  and how do i use it?

I feel like such a newbie. :lolflag:

---

### Post by Seisen on 2007-07-25
sudo is just a command that allows you to have superuser privleges instead of using root.

---

### Post by xubu_caapn on 2007-07-25
some of it might be going to your /swap partition.

---

### Post by Orochi on 2007-07-25
To enter sudo commands open up a terminal window (applications, accessories, terminal) then type 'sudo command'. Enter your password (which wont display on the screen) and press enter.

The reason some of your drive space is missing might be due to differences in calculating size. When most people say GB or gig or gigabyte they really mean "gibibyte" (1 gibibyte = 230 bytes = 1,073,741,824 bytes = 1,024 mebibytes). This is also the definition most software uses. Hard drive manufacturers define a gigabyte as 1,000,000,000 bytes. This discrepancy often leads to drives actually being smaller than you thought they were.

And like xubu said, some of your space will be the swap partition.

---

### Post by linkhows on 2007-07-25
This is what I got does anyone have any idea what this means?
desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
desktop:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61475807232 bytes
255 heads, 63 sectors/track, 7474 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3953    31752441    7  HPFS/NTFS
/dev/sda2            3954        7323    27069525   83  Linux
/dev/sda3            7324        7474     1212907+   5  Extended
/dev/sda5            7324        7474     1212876   82  Linux swap / Solaris

---

