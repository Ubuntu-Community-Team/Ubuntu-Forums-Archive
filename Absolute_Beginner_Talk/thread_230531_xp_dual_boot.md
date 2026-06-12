---
title: "xp dual boot"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by stubblepoo on 2006-08-06
i have xp already on my pc and i want to install ubuntu onto it. i know that i need to partiotion it and i know that you can do this with ubuntu. i dont want to have to reinstall windows so must i partition the pc with another program and then install ubuntu on it or can i just use te ubuntu one?

---

### Post by Jagot on 2006-08-06
You can just use Ubuntu.  Check out the graphical live cd installer here:

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

Or the alternate cd installer from here:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by Phasmagon on 2006-08-06
If you just have one partition (the one with Windows on it) and no second drive, then yes you should use a program like partition magic, to repartition your drive so you do not lose any data on your windows partition. Then you can install ubuntu from the live-CD. Ubuntu does not support drive repatitionning without loos of data on ntfs partitions.

---

### Post by Jagot on 2006-08-06
Don't use Partition Magic - it doesn't play well with Linux.  You can resize your NTFS partition with the partitioners on both of the install CD's with no loss of data.

---

### Post by Herman on 2006-08-06
Ubuntu's installer partitioner in the 'Alternate' CD has been able to partition NTFS drives perfectly well and safely since Ubuntu 'Hoary' Edition came out a couple of years ago now, which is a long time ago in computer terms.
GParted in the new 'Desktop' Live/Install should be able to handle NTFS equally well. 
Regards, Herman :D

---

### Post by xpod on 2006-08-06
This is a subject with many conflicting beliefs with regard to the pro`s and con`s of both "partition magic" AND "gparted".

Prior to installing ununto on a slave drive i had defragged my xp with a veiw to installing it on the same drive.

But after defragging i found i had quite a large blue(relatively) block of seperate data further along the drive than the main data.

This caused concern especially as i did`nt have xp cd in case of calamity.

IF attempting ANY partitioning or indeed REpartitioning make sure you have some way of restoring things if it all goes wrong.And always back up important data!!!!!

GOOD LUCK......Ive got unbunto on slave and X & Kbunto on separate pc.
And at this rate XP will be sacked real sooooooooon in place of something a bit better

Just as soon as ive picked up the basics a bit better...:confused:

---

