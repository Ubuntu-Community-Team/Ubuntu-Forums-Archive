---
title: "How do partitions work?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by nirpius on 2007-04-28
Hi, I know I'm supposed to have some sort of separate partition for Windows (XP) and Ubuntu and another one for a boot loader but I have no idea what these do and what is this swap partition I hear people talking about?

Also, I was wondering if it's possible to create another partition where I can hold all my music and documents so that I can read from and write to it in both Ubuntu and XP.

---

### Post by Metacarpal on 2007-04-28
Think of partitions as apartments.

The hard drive itself is the building the apartments are in.  It has its own street address (hda, for instance).

Each partition is then an apartment.  The apartments are numbered (hda1, hda2, etc).  Different families (operating systems, personal files and data, swap space) "live" in different apartments.  The apartments are also (mostly) fireproof, so if one partition burns down, it doesn't take all of the data in the other partitions with it.  So if you have Windows in hda1, Ubuntu in hda2, and all of your documents, pictures, movies, etc in hda3, and then Windows pulls a blue screen of death, you can reformat hda1 and reinstall Windows without damaging ubuntu or losing your personal files.

Edit: If you want to have your data partition readable by both Ubuntu and Windows, format that partition as fat32.  Windows can't read ext3 (the Ubuntu default) without special drivers, and getting Ubuntu to write in NTFS is tricky, and potentially hazardous to your data.

---

### Post by Bachstelze on 2007-04-28
Nice metaphor here :p My usual one is :

See your hard drive as a cake and partitions as slices of it. Partitions can come in different flavours ans each OS has it's own tastes - for example revent Windows'es like their partition NTFS while Linux hates it and prefers ext3 or reiserfs.

And so on :p

---

### Post by Metacarpal on 2007-04-28
Sorry, hopped up on cold meds, just realized that I failed to answer half your questions.

Here: [very useful site]("http://www.psychocats.net/ubuntu/index.php").  Great links on the left.

That way I can't give you Dayquil-ized misinformation.

---

### Post by nirpius on 2007-04-28
Cheers guys that's brilliant!

Question well and truly answered.

---

### Post by Tomosaur on 2007-04-28
You do not need a seperate partition for your boot loader.

A hard drive has something called a Master Boot Record (MBR) for short. This is where the bootloader gets stored. Grub (the bootloader which is installed with Ubuntu) is installed in two places. The bootloader itself gets stored on the MBR (you don't need to set up the MBR yourself, it already exists), while the configuration files get stored in the /boot directory. Now, it is POSSIBLE to put the /boot directory on its own partition, but it's not required. All you need for a Linux installation is one partition for the system, and one partition for swap.

You should think of swap as 'extra RAM'. Linux will monitor your RAM - when it needs to use more RAM than is available, it stores some of the existing stuff floating around in memory (stuff which isn't currently being used) to the swap space. When these resources are required again, they're read from the swap space and put back into your RAM. Since resources are actually 'swapped' around (Program X's resources are taken from RAM and stored in swap, Program Y's resources are taken from swap and replace X's resources), it's not really the same as having 'extra RAM', but the idea is that you can store more stuff in memory than you can without swap.

The general advice is to have around double your RAM allocated to swap space, but it's on a curve which levels out as you increase your RAM. You are unlikely to need 2GB of swap if you have 1GB of RAM, for example, so you can afford to be conservative. Only when you have small amounts of RAM should you really be concerned about having at least double that amount of swap space.

---

