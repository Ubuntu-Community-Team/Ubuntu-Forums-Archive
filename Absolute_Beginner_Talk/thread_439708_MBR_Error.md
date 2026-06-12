---
title: "MBR Error?"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Skillz_NoOdLeS on 2007-05-10
I tried to install ubuntu.
when i boot  from the cd with the ubuntou iso, i get MBR Error on my screen

help please =)

---

### Post by confused57 on 2007-05-10
Here's an excellent guide for burning an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Make sure to do a md5sum check of the downloaded iso...if the md5sum is correct, burn the iso to cd as an "image", not as a data cd or bootable cd...burn at a slow speed(8x or less)....make sure to set your cd drive as the first boot device in bios.

---

### Post by bobplano on 2007-05-10
well mbr refers to how it boots up. do you have any dual-booter like GRUB already on there? you might also check your BIOS. you might also do an md5sum and hash check on it. what speed did you burn at? other than that i don't know how the mbr would affect the cd

---

### Post by Skillz_NoOdLeS on 2007-05-10
i did a md5checksum, and they matched. i actually think its my master boot record.

i tried to install another os a while back on the same hd and it didnt go so well

im not duel booting, so grub isnt a issue.

does anyone know of a program that i can use to clear my masterboot record without haveing to boot into a os first



sorry if that was confuseing, im new to this linux thing =p

---

### Post by bobplano on 2007-05-10
well if your already using windows you can put in your xp cd and go to recovery mode and type in fixmbr. there are also other solutions on the internet.

---

### Post by Skillz_NoOdLeS on 2007-05-11
i dont have my xp cd anympore =/ . 

and its a new harddrive, with a messd up master boot record

---

