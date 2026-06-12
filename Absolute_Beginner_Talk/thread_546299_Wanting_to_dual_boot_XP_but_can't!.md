---
title: "Wanting to dual boot XP but can't!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Goodkimchee on 2007-09-08
Okokok, so I'm an idiot, yes.  Now that's straight, could someone please help me!  

I installed Ubuntu Feisty, created a partition, told it where to install.  During the install process there was no mention of the NTFS partition or migrating any info or whatnot.  So now, when I boot up, XP is not an option to boot and Ubuntu doesn't recognize the NTFS partition.  At all.  I've gone to several different pages looking for help, the most recent being [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) which, while kind of helpful, wasn't really.  I made a SuperGRUB disk and tried using that to figure my way through, but I get a BSOD for half a second and then it just reboots, over and over and over.  So I used the SuperGRUB disk to get me booting back into Ubuntu at the very least.  

Compaq Presario R3000, Athlon64 3000+ processor, GForce 2Go 420, 500mb Ram.  

Once again, HELP!

---

### Post by Marc Hoffman on 2007-09-08
If you use gparted can you see the NTFS partition?

---

### Post by Topes_the_one on 2007-09-08
Having similar problem.  Trying to install with win xp pro already loaded.  Received the following message " /bin/sh: can't access tty;  job control turned off.  What does this mean and how do I fix it?  The Ubuntu disk is all right.  It loads on other similar systems.  

Topes_the_one

---

### Post by oilchangeguy on 2007-09-08
> **Topes_the_one said:**
> Having similar problem.  Trying to install with win xp pro already loaded.  Received the following message " /bin/sh: can't access tty;  job control turned off.  What does this mean and how do I fix it?  The Ubuntu disk is all right.  It loads on other similar systems.  

Topes_the_one

google the error message. there's lots of info on it.

---

### Post by Goodkimchee on 2007-09-08
Ok.  First off, what is gparted?

I tried to "mount" the drive, but it still won't let me look inside it or anything.

---

### Post by Marc Hoffman on 2007-09-08
gparted is a partition manager available via add/remove. It allows you to view and modify partitions. 

This can be done using the live disk you installed Ubuntu from.

My advice would be to boot from the live disk and use gparted to view the hard drive. It should mouont all the partitions and open a folder for each on the desktop. This way you can check if XP is still there.

---

### Post by Goodkimchee on 2007-09-08
it won't let me apt-get gpart from the live cd!

---

### Post by Marc Hoffman on 2007-09-08
It should already be on there- look under System-Administration-GNOME Partition Editor

---

### Post by Rupertronco on 2007-09-08
I'd recommend partitioning with the gparted live cd, which you can get from their site, Sometimes the live cd mounts the drives it ends up trying to format/partition and it becomes obnoxious.

---

### Post by rickycodie on 2007-09-08
no no he's saying to boot off the live cd. then go to system admin and the first option is gparted. from there it should be obivous.

---

### Post by mramsey on 2007-09-08
I found it easier to just download gparted from their website and then set the partitions up.  Then I used the feisty alternate insttall iso to install ubuntu.

believe me it sounds harder than it is.

---

### Post by Goodkimchee on 2007-09-08
aaaaah.  Now i get it.  

Ok.  it tells me that "The contents of disk 1 cannot be displayed."  That's the partition where XP should be. Now I haven't deleted anything from it or formatted it or anything like that.

So now what?

---

### Post by Goodkimchee on 2007-09-08
Okowaitaminute. Crap.  Sorry, wrong screen.  

Ok, so I'm looking at /dev/hda - GParted.  the first partition is /dev/hda1 which is an ntfs filesystem and 37.44GB in size, where 7.86 GB is used, and under flags it says 'boot.'  When I right click on it and go down to Information, it says its status 'not mounted.'  

so, NOW what do I do?  I'd imagine that I would mount it, but all the mounting helps I've been going through really haven't been all that helpful.  So what so I do to mount this?

---

### Post by Yizi on 2007-09-08
The best option is install Windowns XP first then Ubuntu that way nothing goes wrong :)

---

### Post by eapache on 2007-09-08
Please run the following in a terminal (Applications>Accessories>Terminal) from the installed copy of ubuntu and post the file that opens.```
gedit /boot/grub/menu.lst
```

---

