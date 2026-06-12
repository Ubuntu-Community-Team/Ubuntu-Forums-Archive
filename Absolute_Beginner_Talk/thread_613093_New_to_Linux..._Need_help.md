---
title: "New to Linux... Need help"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by diirka on 2007-11-14
Ok so here goes, I installed ubuntu a couple months ago.  I havent even had a chance to turn my laptop on since then until yesterday.  I updated everything and upgraded to gutsy.  Now I see that there is a ubuntu ultimate 1.5.  Is it a good idea to go with this version?  I read that it has all the wireless stuff straightened out.  Also I partitioned my hard drive so I could run both windows and linux but I like linux so much I want to go ahead and partition the whole hard drive for it.  Do I need to completely reinstall ubuntu or can I repartition it without loosing everything?  Thanks for the help in advance.

---

### Post by bigken on 2007-11-14
I suppose you could use the gparted live cd to resize your hdd to create a partition

---

### Post by diirka on 2007-11-14
So would it be a good idea to just reformat the whole hdd and install using the whole thing instead of the partition?  Also what do you guys think about the ubuntu ultimate 1.5?

---

### Post by CatKiller on 2007-11-14
Even if the partition takes up the whole drive, it's still a partition. So there's no real difference between installing again and just moving the partition you've got around, other than one of them loses your existing stuff.

You'll need to use a live cd - either the Ubuntu install cd or the [GPartEd live cd]("http://gparted.sourceforge.net/") - since you can't edit a mounted partition, so you can't use your normal environment.

You'll need to delete the partitions that you don't want, move the partition you do want to the start of the drive, and then make the partition larger.

You may need to edit **/boot/grub/menu.lst** to point the boot process to the correct partition, and you may need to edit out any lines in **/etc/fstab** that refer to your other partitions if you had your Windows partition automatically mounted.

Good luck, whichever you choose.

---

### Post by ricanelite on 2007-11-14
i would say this, if you have any data back it up if you can. Then I will just do a full install of Ubuntu  and thats it. If you just want Ubuntu Linux there. Just like how I did on my Desktop PC which I just got a couple of months ago.

Now it is just waiting for a graphics card.

---

