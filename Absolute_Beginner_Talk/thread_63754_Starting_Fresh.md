---
title: "Starting Fresh"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by Unit #134679 on 2005-09-08
Whats an easy way to reinstall Ubuntu and start fresh without reformatting?

---

### Post by aysiu on 2005-09-08
[QUOTE=Unit #134679]Whats an easy way to reinstall Ubuntu and start fresh without reformatting?[/QUOTE] Isn't reinstalling Ubuntu, by definition, reformatting? Your best bet is to have a separate /home partition. That way your settings and preferences all stay even when you reinstall the OS.

---

### Post by poofyhairguy on 2005-09-08
[QUOTE=Unit #134679]Whats an easy way to reinstall Ubuntu and start fresh without reformatting?[/QUOTE]

Yep. Split your drive into a /home and / (root) parition. You need about five gigs for the root one, and the rest for /home. I bet Gparted can do it. Just break off the 5 gigs from free space.

(sudo apt-get install gparted then look in system tools)

Then put in the install CD. Manually edit the partition tables. The select the bigger side and hit enter. Set it as home, but don't let it format it. Then select the 5 gig part to be root. Tell it format that part. Continue with install

Then whenever it goes to teh desktop, go and delete the non home stuff out of home partition.

gksudo nautilus 

is the command to help you with that. And for the future, you can just format the root part and keep your settings. 

its easy, and its what I do.

---

### Post by Unit #134679 on 2005-09-09
[QUOTE=poofyhairguy]Yep. Split your drive into a /home and / (root) parition. You need about five gigs for the root one, and the rest for /home. I bet Gparted can do it. Just break off the 5 gigs from free space.

(sudo apt-get install gparted then look in system tools)

Then put in the install CD. Manually edit the partition tables. The select the bigger side and hit enter. Set it as home, but don't let it format it. Then select the 5 gig part to be root. Tell it format that part. Continue with install

Then whenever it goes to teh desktop, go and delete the non home stuff out of home partition.

gksudo nautilus 

is the command to help you with that. And for the future, you can just format the root part and keep your settings. 

its easy, and its what I do.[/QUOTE]

Oh wow thanks. I'll do that when I come back from outta town. Thanks

---

