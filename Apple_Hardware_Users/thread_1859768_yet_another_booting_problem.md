---
title: "yet another booting problem"
date: 2011-10-14
forum: Apple Hardware Users
---

### Post by jeffisabelle on 2011-10-14
Hello guys,

i know there are too many booting problem posts in the forum but none of them could help me so i decided to create a new one. please don't take this as spam. 

i have been using my imac with ubuntu for almost 1 year. it was perfect and i had no problem, until i decided to make a triple-boot with win7 :) 

i have repartitioned my drive and and tried to install windows7. it failed, of course. but it also damaged my system. now i am not able to boot ubuntu. for 3 days i have been trying all the things that are written on the forums, but i really couldn't solve the problem. 

first, i got a frozen tux logo when i try to boot ubuntu from refit. then i boot with gparted and deleted the ntfs partition, reformatted it to ext3 and merging it to my ubuntu partition (sda4) i hoped getting everything same as 3 days before could solve the problem. but it couldn't. now i have a gray windows like icon on refit instead of tux logo and it says boot legacy os from hd. if i try to boot it, it frozen like tux logo, but when i try to boot from  apple boot thing (with holding option key) it says "missing operating system, no bootable device blabla"

i have tried synchronize the tables, didnt work.
i have also tried restoring mbr and reinstalling grub with boot-repair-disk with every combo of options, (reinstalled grub on sda and sda4, tried to restore mbr on efi, mac and linux parts) they really don't work. 

i also boot with live ubuntu cd, and tried to setup grub from terminal. but i failed again. 

please show me another way to fix this. or at least tell me what is the reason that i can't boot ubuntu. (i can boot macos) 

i have backed up my personal files with live cd, i will just reinstall ubuntu if i can't fix this, but i'm afraid of ending up with the same result. 

sorry for the long post, i thought giving the details can help you guys determine the problem. if you need more information let me know.

---

### Post by jeffisabelle on 2011-10-14
[http://askubuntu.com/questions/64771/can-no-longer-boot-with-refit-and-grub-on-early-2006-macbook-pro](http://askubuntu.com/questions/64771/can-no-longer-boot-with-refit-and-grub-on-early-2006-macbook-pro)

this thread did the trick for me. if anyone has the same problem just follow the given answer.

---

