---
title: "Partitioning"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by mofokuban on 2007-04-19
Hello all.  I've had some experience with Linux and Ubuntu.

Recently, a friend mentioned that I should share my home directory between two distros.

I have a 250 GB SATA drive (really, it's 232 GB).

I'm going to have my drive partitioned like this:

HDD0 - Grub, ext2
HHD1 - Windows XP, NTFS, 60 GB
HHD2 - Swap, linux-swap, 2 GB
HDD3 - /home, ext3
HHD4 - Ubuntu
HHD5 - MEPIS

Now, my question is this: what is the amount of space I need for Grub, and what is the recommended amount of space for Ubuntu and MEPIS?  I think 20 GB each should cover software and updates and give me plenty of breathing room; the rest of the space would go to the /home directory.

Thanks!

---

### Post by siciliancasanova on 2007-04-19
I have 20GB for my Ubuntu and the rest is for home and I have not run into any problems as far as upgrades and installs (beryl and the whole works)

---

### Post by mofokuban on 2007-04-19
I'm pretty confident that it will be more than enough space, but I just want to be sure.  I remember being incredibly frustrated when I failed to give enough space to XP when I partitioned the drive incorrectly (didn't leave enough space for SP2).

Thanks for your opinion!

---

### Post by Patrick K on 2007-04-19
You need not worry about grub's space. The entire /boot directory (grub is in a subdirectory) is only about 15 meg. The Grub folder is only 164 KB or so.. The boot loader itself resides in a very small hidden partition called the boot sector (it's part of the disk space lost to operational overhead when you format the drive). So no special actions are needed. Just let it reside on the main Linux install.

---

### Post by Wim Sturkenboom on 2007-04-19
May I suggest that you add one more partition for the windows data. I would make WinXP approx 15GB and use the rest of the 60GB that you already planned for a data partition that will include the MyDocuments.
If you ever have to reistall WinXP, you will be able to keep your data safe.

Further, before you start sharing /home, make sure that you will not encounter problems due to different userIDs (not likely as Mepis is nowadays based on Ubuntu) and the other stuff related to e.g. GTnome versus KDE. I think Mepis is KDE based (not sure) in which case you might end up with a Kubuntu instead of Ubuntu.

From experience:
I installed RedHat 8.0 on a system and next Mandrake (this is long ago). Both use Gnome but by sharing the  /home, the appearance of Gnome in RedHat all at a sudden changed after the first boot into Mandrake.
So there might be little issues.

---

### Post by mofokuban on 2007-04-19
MEPIS is KDE based.

That's a good point... I hadn't though of that.

Maybe I'll just set them up to use the same swap and keep the /home directories separate for each install.

Thanks again.

---

### Post by mofokuban on 2007-04-19
Here's the thing I want to achieve with this.

Ubuntu is currently what I use the most.  Recently, though, I've booted up in Windows just because I have a massive amount of files to sort through.

I am keeping Windows solely because of the integration it has with everything; it is everywhere on a college campus.  I am going to keep all of my closed-source applications and file formats on there (my music collection in MP3, etc.)

I will primarily use Ubuntu, and I like trying other distros for no other reason than to just experience them.  It's the same attitude I have towards food (I went vegetarian last semester, and made it a goal to try as many veggie foods as I could).

The reason I wanted to have a /home directory that could be shared was because I didn't want to go through the trouble of setting up access to my Ubuntu /home each time I try out a new distro.  I figure it would be easier to have it shared right off the bat so I could conserve hard drive usage with my files and such.

I plan on doing this once I migrate to a MacBook and OSX 10, and discarding Windows more or less permantly

---

