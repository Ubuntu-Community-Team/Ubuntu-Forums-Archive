---
title: "How do I create a FAT32 partition?"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by STINGRAY on 2005-08-29
Hello fella´s

I´m looking to install Ubuntu on to my single hd with XP installed on it already. So I read and read these forums and understood that it´s a good idea to have a FAT32 partition to be able to access files from xp to linux and vice versa.

I know that when I install Ubuntu I can choose to manually partition the drives for the root, swap, boot and home partitions. But how do I create the FAT32 partition? Can I do this in the installer as well?

Any help would be much appreciated, thanks

/"Linux-noob"

BTW, is this too many partitions and are the sizes ok?:

XP: 26GB
ROOT: 7GB
BOOT: 100MB
SWAP: 512MB
HOME: 15GB
FAT32: 5GB

---

### Post by KingBahamut on 2005-08-29
Not sure about doing it with the installer. 

I know once you get it installed you can use parted or qtparted to create the partition, thats what I would probably do in this situation. 

Are you wanting to create a fat32 part for access from one system to another?

---

### Post by STINGRAY on 2005-08-29
[QUOTE=KingBahamut]
Are you wanting to create a fat32 part for access from one system to another?[/QUOTE]
Yes, I understood that would be a wise decision...or?

---

### Post by KingBahamut on 2005-08-29
Just install it as is, edit your fstab to access your NTFS drive from your Ubuntu partition. Im assuming thats where your going to draw from anyway, moving files from your windows part to your linux part. 

That is very easy to do.

---

### Post by STINGRAY on 2005-08-29
But if I want to move files from Linux to XP it would have to be a FAT32 partition, right?

---

### Post by KingBahamut on 2005-08-29
That is correct. 

Though Id never do it.

---

### Post by az on 2005-08-29
"Hello fella´s"

What about the women?


I beleive you can create a fat partition with the installer.  You can even give it a label and have it mounted at boot time.  Just pick manually edit parttion table and then shrink an existing partition to make some free space.  From that free space, make your fat partition and give it a label.

Use "guided partitioning" to let the installer create your root and swap partitions automagically out of the remaining free space.  

There is no need to make seperate root, home, and whatnot, just put everything on the same partition (unless you have speacial needs, but if you were aware of such special needs, like for a webserver, you would not be asking this question)

You can always just install Ubuntu on some free space and then go back and create some more free space to use as a fat partition.  You would be able to format it afterwards...

---

### Post by STINGRAY on 2005-08-29
Thanks, much appreciated. Now I´ll get to work and install Ubuntu. Wish me luck, I may need it...  :roll:

---

### Post by KingBahamut on 2005-08-29
Your better than I am azz. 

Its morning here and Im not awake yet. 

What the heck is a Clinical Perfusionist?

---

