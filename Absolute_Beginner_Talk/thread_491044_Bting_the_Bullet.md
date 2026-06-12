---
title: "Bting the Bullet"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-07-03
Hi

I currently have a dual boot with XP and Feisty. I have had a couple of gremlins within each OS, and although they don't cause a lot of problems, I can't get rid of them. I thought I would go back to the beginning and start over. Another reason for this is to make a /home partition which I didn't do initially as I was completely new and didn't understand the whole concept. I have backed all the data I need (I think) and want to give it a go, but I have a couple of questions.

Is having the home partition different to the share partition or can I combine the two?

I use XP predominantly for games or else I would probably shift to Ubuntu entirely, but could someone give me arough idea of partition sizes on a 120g harddrive and what extensions they should be?

I did have both systems able to read / write to each others systems which was fine. I take it that the share partition would put it all in one place?

thanks in anticipation

gazzadtfan

---

### Post by apunc1 on 2007-07-03
> **gazzadtfan said:**
> Hi


Is having the home partition different to the share partition or can I combine the two?
gazzadtfan

You can combine the /home and shared data partition and format it Ext3 by using FS Drive, a small program that allows Windows to read from and write to Ext3 partitions. That way you wouldn't need a FAT32 partition for shared and Ext3 for /home.

> **gazzadtfan said:**
> 
I use XP predominantly for games or else I would probably shift to Ubuntu entirely, but could someone give me arough idea of partition sizes on a 120g harddrive and what extensions they should be?
gazzadtfan

Thats a good size hard drive.You should probably allow 20-30 gb for your / partition. /swap should be twice your ram size, though I wouldn't go more than 2gb.
XP would be formatted NTFS, / Ext3, swap /swap, /home ext3 and /shared fat32 (unless you are using FS drive mentioned above so you would need just one partition for /home and /shared that would be ext3.)

---

