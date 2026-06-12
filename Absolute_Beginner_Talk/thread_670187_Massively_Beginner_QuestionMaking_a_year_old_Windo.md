---
title: "Massively Beginner Question:Making a year old Windows laptop dual-boot w/ Ubuntu"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by clarity on 2008-01-17
Okie....I've had my current laptop for little over a year: dell inspiron 1505 core 2 duo 1.83 Ghz 1 gb ram and a 512 mb mobile-type gpu running Win XP home media center edition 2005.

oh right, and a 105 gb HDD. of which just under 50 gb is already used.

i'd like to make my laptop dual boot with Ubuntu, setting out about 20 gb of my remaining space for it, and maybe a 8-10 gb block for moving files between the 2.

Windoze will continue to be my primary OS with ubuntu more to keep my knowledge fresh-ish. especially on IT security.

so here's the thing: i got no idea how to go about this since ive never done any partitioning in my life. i read quite a few threads here including [this]("http://ubuntuforums.org/showthread.php?t=282018&") and its all as clear as a pint o' guiness.

starting clean is not an option. Programs and data already existing on the laptop need to stay as-is, some partition-manipulation done on the remaining space, ubuntu added with (obviously) the ability to dual boot.

so yeah, any help is appreciated.

---

### Post by koleoptero on 2008-01-17
You can use gparted from the ubuntu live cd to resize the partition and leave 20GB of unallocated space for linux. Then you create your linux partitions. You'll need 1gb of swap probably (because of the ram you have) and the rest you can either have a large / drive or two partitions / and /home if you want your settings to be saved. I suggest 8GB for / and the rest for /home. You don't need any intermediate partition to move files between windows and linux cause ubuntu will mount the windows partitions you have and you will be able to read/write on them.

---

### Post by Joeb454 on 2008-01-17
Don't forget to defragment (a good 2 or 3 times at least) your Windows partition first.

Also, I'd recommend backing up all your important data, partitioning can and may very well go wrong. I've never had any problems, but I know people who've done it and corrupted the entire hard drive (it couldn't even be rescued).

So Defrag, Backup, and be careful :)

---

### Post by hyper_ch on 2008-01-17
Have a read here:  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by clarity on 2008-01-17
> **koleoptero said:**
> You can use gparted from the ubuntu live cd to resize the partition and leave 20GB of unallocated space for linux. Then you create your linux partitions. You'll need 1gb of swap probably (because of the ram you have) and the rest you can either have a large / drive or two partitions / and /home if you want your settings to be saved. I suggest 8GB for / and the rest for /home. You don't need any intermediate partition to move files between windows and linux cause ubuntu will mount the windows partitions you have and you will be able to read/write on them.

i think i can get gparted stand alone right? i dont want to get the ubuntu live cd _just_ for gparted. 

ok...so i need to make a) non-NTFS-ed space for Linux and within that : b,)1 gb swap (whats that for btw?) c) 1 partition for / and d) 1 partition for /home

are you sure ubuntu can read NTFS? i read different here and there.

[dumb question]
also, i just use gparted, make the partitions,boot from ubuntu CD (non-live) install and i'm done. does the dual-boot thing just happen if there are 2 OSs?
[/dumb]

[quote=joeb454]Don't forget to defragment (a good 2 or 3 times at least) your Windows partition first.

Also, I'd recommend backing up all your important data, partitioning can and may very well go wrong. I've never had any problems, but I know people who've done it and corrupted the entire hard drive (it couldn't even be rescued).

So Defrag, Backup, and be careful [/quote]
done, and done. computers aren't anything new to me :D just this partitioning thing. + the fact that i got 12 gb of music to look after makes it harder.

[quote=hyper_ch]
Have a read here: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[/quote]

cool, i'll read up on that a bit.

---

### Post by dstew on 2008-01-17
> does the dual-boot thing just happen if there are 2 OSs?No. You have to approve the grub booter installation. If you have only one disk, when the installer asks for permission to install grub to the MBR, which in its language is (hd0), tell it yes. Then it should be left in a dual-boot configuration. If you decline to install grub, you can install it later, but  you won't be able to boot Ubuntu until you do.
EDIT: There is a problem installing grub on some Dell laptops. See [this]("http://ubuntuforums.org/showthread.php?t=668740").

---

