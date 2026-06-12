---
title: "How will installing Ubuntu affect my files?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by DrunkPeanut on 2007-04-26
I realize that this is probably a really stupid question, but I can't seem to find the answer on my own...
When I select a partition to install Ubuntu on- does it make it inaccessible under Windows (by deleting and/or using a different file system)?
I ask this because I have a small partition on which my Windows and other important programs are installed on, and a  larger partition which holds my files.
I want to install Ubuntu on my larger partition but still be able to access the files on it through Windows, preferably without splitting it. Can it be done, or do I have to start burning all my data to CDs in case I decide I want to fall back to Windows?

Thanks in advance :)

---

### Post by Cypher on 2007-04-26
Ubuntu will format the partition to EXT3 and that will make Windows not inherently be able to access the files/partition. There are few prorgams out there for Windows that will allow you to read the EXT3 partition, but not natively.

You really should re-size the larger partition to make some room for Ubuntu..

Making a backup of your data before you do any of these things would be a VERY smart idea..

---

### Post by lluisanunez on 2007-04-26
When you select a partition to install Ubuntu on, it gets reformatted. So your files would be lost. You must make room for a new separate partition for Ubuntu, and before that backup your files.
If you leave an NTFS partition for these files, you will be able to access them from Windows and from Ubuntu (installing ntfs-3g)

---

### Post by straps on 2007-04-26
You can resize your data partition during install selecting "manual partitioning" and create a swap and a root (/) partion for Ubuntu; the installer will install GRUB as the boot loader that will let you select the OS at startup.

If you install Ubuntu on the data partition...Yes, Ubuntu will format it...but in feisty, modify the partition table is very simple.

Do a backup before, bie

---

### Post by DrunkPeanut on 2007-04-26
Thanks! Wow I've never gotten answers this fast on any forum before :P
Well, I'd better start moving some files around...

---

### Post by Cypher on 2007-04-26
We strive to be like any other forum you've ever visited..and most of us have no lives..:)

---

### Post by Josey on 2007-04-26
my setup is as follows

ntfs windows xp partition 20 gb - C:\ in windows
ext3 ubuntu partition 20 gb - /
ext3 ubuntu partition 200 gb - /home
linux swap - 2 gb

In my experience this makes for a great setup.
/ is where the linux OS is installed
/home is where ubuntu puts personal files and seperating ' / and /home ' on different partitions makes formatting the OS very painless if you run into problems. 
Hope that's helpful and not just gibberish to you heh.

---

