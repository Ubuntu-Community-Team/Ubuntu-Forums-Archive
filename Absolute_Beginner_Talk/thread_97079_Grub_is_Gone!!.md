---
title: "Grub is Gone!!"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by Cud on 2005-11-30
Hello I treid to install a new Seagate ultra ATA/100 300gb hard drive as a slave for my hoary /windows ME dual boot system. I didnt have the right devuice drivers so I made 1 137 gb partition in FAT32. Then I shut down and tried to reboot. I got some weird blue stripe and propaganda from the disc utility CD I used to format the HD, and then STRAIGHT TO WINDOWS!!!!
What happened to my GRUB menu???
How do I get back to Ubuntu??
Thanks

---

### Post by Robgould on 2005-11-30
The "propaganda" re-wrote the disks mbr.  This got rid of grub.  To get back to ubuntu, you need to boot from the install disk in rescue mode.  From there you can re-install grub.

---

### Post by Cud on 2005-11-30
Thanks for the Help
I´m not exacty how sure how to re-install GRUB. When I used rescue mode I chose (I think) the root partition. Then I apt-get install grub, but then I was told that grub is already at the newest version.
Is this what you meant by installing grub?

Out of curiosity what is a "mb"?
Thanks

---

### Post by Robgould on 2005-11-30
This link should help you:
 
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253")
 
or you can serach the forums for "reinstall grub".  You will get a lot of hits.
 
mbr = master boot record.  It is the part of the disk that your computer uses to boot.  Normally grub is installed to the mbr.  So when you restore the mbr, you overwrite grub.

---

### Post by frodon on 2005-11-30
To restore your GRUB : [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Good luck ;)

---

### Post by Cud on 2005-11-30
Many thanks..
Grub is again restored to its former glory...

---

### Post by Robgould on 2005-11-30
Glad you are fixed.

---

