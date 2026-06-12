---
title: "Help with partitioning"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by a_pint_of_milk on 2006-05-31
Hello all. I've decided to give linux a try and Ubuntu 5.1 looks like a safe bet. I currently use windows (sorry) and my drive configuration is as follows:

SATA Maxtor 160gb (Windows installation drive)
IDE Maxtor 160gb (Holds mp3s and general download stuff)
IDE Maxtor 20gb (blank)

To try Ubuntu, I was going to use the 20gb drive. I've saw the installation guide at [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm) and it looks pretty thorough. I was just wondering if anyone had an idea of what my partitions (and sizes) should be if I want to install onto the 20gb drive?

Oh and am I better using the Ubuntu 5.1 DVD or CD install?

---

### Post by rcarring on 2006-05-31
I have heard that SATA drives won't accept grub, and that this has to be installed on the Linux partition (i.e. the 20GB hard disk). One comment I can make is that slaving this ide to your dvd/cd/cdr/rw drive will make it run a lot slower.

However, you have the article that tells you how to go about this, so let Ubuntu decide the split of partitions.

If both your main drives are formatted with NTFS then you'll be able to read but not write to these drives without a special driver.

---

### Post by catlett on 2006-05-31
You should make a / (root), a swap and a home.
The swap is usually twice your ram i.e. 256mb ram = 512mb swap
I don't know your ram but you won't need more than 512mb swap regardless of your ram if your not doing video editing or anything extreme.
Root will handle your installation files. The base system and anything else you add. I am using about 3.5 gb but I had it up to 7gb before when I loaded  numerous window managers   i.e. gnome, kde,xfce. So I guess 8gb would be safe.
Leaving the balance for home. 
 I guess I would go 
swap    500mb
/ (root) 8gb
home   11.5gb
It doesn't have to be an exact number. Just as long as you have at least 3gb for root you can do whatever else to your preference.
There is a good link in my signature for a Dapper install. Good luck.

Edit: I am not sure about the sata issue mentioned above (I didn't notice the post when I started replying) but if it is true you can install grub to a floppy to be safe . This way you boot to the floppy with grub and it will send you to the ubuntu install, bypassing the sata altogether. I would google the sata/grub issue to be sure. I don't have one.

---

### Post by nanotube on 2006-05-31
[QUOTE=a_pint_of_milk]Hello all. I've decided to give linux a try and Ubuntu 5.1 looks like a safe bet. I currently use windows (sorry) and my drive configuration is as follows:

SATA Maxtor 160gb (Windows installation drive)
IDE Maxtor 160gb (Holds mp3s and general download stuff)
IDE Maxtor 20gb (blank)

To try Ubuntu, I was going to use the 20gb drive. I've saw the installation guide at [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm) and it looks pretty thorough. I was just wondering if anyone had an idea of what my partitions (and sizes) should be if I want to install onto the 20gb drive?

Oh and am I better using the Ubuntu 5.1 DVD or CD install?[/QUOTE]
well, if you want to be really simple about it, you can just make one big 20g partition for ubuntu (just do the "automatically partition option). if you want a separate /home (this is not a bad idea, in case you have to reinstall the os, all your docs and prefs will stay untouched in /home), then give about 5 gigs to /, another  512 megs to swap, and all else to /home.

---

### Post by nanotube on 2006-05-31
[QUOTE=catlett]You should make a / (root), a swap and a home.
The swap is usually twice your ram i.e. 256mb ram = 512mb swap
I don't know your ram but you won't need more than 512mb swap regardless of your ram if your not doing video editing or anything extreme.
Root will handle your installation files. The base system and anything else you add. I am using about 3.5 gb but I had it up to 7gb before when I loaded  numerous window managers   i.e. gnome, kde,xfce. So I guess 8gb would be safe.
Leaving the balance for home. 
 I guess I would go 
swap    500mb
/ (root) 8gb
home   11.5gb
It doesn't have to be an exact number. Just as long as you have at least 3gb for root you can do whatever else to your preference.
There is a good link in my signature for a Dapper install. Good luck.

Edit: I am not sure about the sata issue mentioned above (I didn't notice the post when I started replying) but if it is true you can install grub to a floppy to be safe . This way you boot to the floppy with grub and it will send you to the ubuntu install, bypassing the sata altogether. I would google the sata/grub issue to be sure. I don't have one.[/QUOTE]
hehe catlett, you beat me to it. :) 
though i would reduce the / from 8 gig to 5, since i can't see how you can use up 8 gigs with system and software (my current ubuntu breezy install is about 3 gigs, with docs and everything)

---

### Post by catlett on 2006-06-01
[QUOTE=nanotube]hehe catlett, you beat me to it. :) 
though i would reduce the / from 8 gig to 5, since i can't see how you can use up 8 gigs with system and software (my current ubuntu breezy install is about 3 gigs, with docs and everything)[/QUOTE]
I couldn't remember what I had it up to before so I didn't want to make a critical error. That's why I put 8 but said I'm up to only 3.5.  AHA! Now I remember. I remembered my partition being used 7gb or so when I would view it in gparted. That's why I mentioned it, but now I remember that was before I made a home partition and everything was in one partition. BTW What is a safe root to tell someone to make? I wanted to say 5gb is plenty if you have a home but that 7g stuck in my head and I didn't want to lead someone astray and they run out of room later on. Is it safe to say 5gb for root when you have a home? It's a common question and since I have your attention I though I'd get the good word from you.:D  Anyways hope to see you posting more, I always learn something when your in a thread. [do you like my coffee cup?:cool: ]

---

### Post by nanotube on 2006-06-03
[QUOTE=catlett]I couldn't remember what I had it up to before so I didn't want to make a critical error. That's why I put 8 but said I'm up to only 3.5.  AHA! Now I remember. I remembered my partition being used 7gb or so when I would view it in gparted. That's why I mentioned it, but now I remember that was before I made a home partition and everything was in one partition. BTW What is a safe root to tell someone to make? I wanted to say 5gb is plenty if you have a home but that 7g stuck in my head and I didn't want to lead someone astray and they run out of room later on. Is it safe to say 5gb for root when you have a home? It's a common question and since I have your attention I though I'd get the good word from you.:D  Anyways hope to see you posting more, I always learn something when your in a thread. [do you like my coffee cup?:cool: ][/QUOTE]

well, i'd say 5 g for root is quite safe, unless you know you plan on downloading and installing a lot of /large/ software packages, or you expect to run a server generating a lot of logs (in which case you really should have a separate /var/log, anyway). i can't see it eating up 5 g. but of coures, if you are doing this on a 200g drive, and have g's to spare, you might as well give 10g to root, just because you can :)
yea, the coffee cups are nice :D

---

