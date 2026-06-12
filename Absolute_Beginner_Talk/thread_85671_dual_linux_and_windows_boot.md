---
title: "dual linux and windows boot"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by thefreak on 2005-11-03
hello
i have a windows xp os and i had instaled linux ubuntu  but the dual boot isn't working
my d partition has become c and the former c has no letter and i have a message "the partition crosses the 1024 cylinder boundary and may not be bootable"
how can i make the dual boot to work properly?
also the c partition is 10 GB large and the hdd is 40 gb 
the linux partition is 6.1 gb and the swap 500 Mb

---

### Post by Kapre on 2005-11-03
[QUOTE=thefreak]hello
i have a windows xp os and i had instaled linux ubuntu  but the dual boot isn't working
my d partition has become c and the former c has no letter and i have a message "the partition crosses the 1024 cylinder boundary and may not be bootable"
how can i make the dual boot to work properly?
also the c partition is 10 GB large and the hdd is 40 gb 
the linux partition is 6.1 gb and the swap 500 Mb[/QUOTE]

thefreak - I think your problem is because the partition that you placed linux is on the last end of the hd (that's the reason why d has become c and c has no letter - is your xp still bootable?). It's like this, say you divide your hd into #1 is your xp and #2_ and #3 linux and #4 swap. Can you place linux on #2 and swap on #3 so #4 (which is on the last end of the hd will be free).

K

---

### Post by paddyg on 2005-11-03
[QUOTE=thefreak]hello
i have a windows xp os and i had instaled linux ubuntu  but the dual boot isn't working
my d partition has become c and the former c has no letter and i have a message "the partition crosses the 1024 cylinder boundary and may not be bootable"
how can i make the dual boot to work properly?
also the c partition is 10 GB large and the hdd is 40 gb 
the linux partition is 6.1 gb and the swap 500 Mb[/QUOTE]

i wonder how you managed to make win xp aware of ubuntu being installed...
my windows ignored what was happening to any ext3 partitions.

you didn't use fat32, did you?

(i've got:
---primary---
hda1 --windows---ntfs
---extended----
hda5---linux---ext3  /boot
hda6---linux---swap
hda7---linux---ext3 /
hda8---linux---ext3  /home [to the very end of the disk])

---

