---
title: "Simple help with partitioning"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Psyik on 2007-03-11
I'm new to Ubuntu (and to all of Linux for that matter), but I've finally decided to get off my lazy butt and try it out. I've decided to start with 6.06.1 since it's a long term support edition. I tried out a few things from the live CD, and everything works. So I'm ready to begin, but first I need to install the thing!

And here is where I need some help. I've been using Windows for a very long time, and I'm used to how it works. More importantly, I can't seem to understand how Linux displays partition data. My harddisk is partitioned like so:

[INDENT]	C: - FAT32 - 27.94 GB
	D: - NTFS - 83.82 GB
	E: - NTFS - 83.82 GB
	H: - NTFS - 83.88 GB[/INDENT]

I'm ready to give H: over to Ubuntu, but I'm not sure how. I've emptied out all the data, but there are still 133 MB of Windows system files left over. So, my main questions:

[INDENT]Can I simply tell Ubunutu to install on H: or do I need to remove that extended partition and let Ubunut recreate it? Or is the process something different? I don't mind putting work into getting Ubuntu up and running, I just want to do it without effecting Windows and C:, D:, and E:.

If I can, do I need to completely clear this drive out? If so, how should I format it? Will a simple NTFS with default allocation size (4096) do, so is there more to it?[/INDENT]

I'm sure the solution is fairly simple, but this is my main rig. And while I normally wouldn't going through trial and error to figure these things out, I don't want to risk the data on the remaining Windows partitions (although I did back up all of the important things). Thanks for reading, and I hope my next post will be through Firefox (actually... I already use Firefox, but you know what I mean)!

P.S. I'm aware that there are pages of documentation, and I've looked them over, but just like the hundreds of posts before me, and the thousands to come, I'm too worried that I'm going to do it wrong, and don't want to risk gigs of old data and years of using this installation of XP if I don't have to.

---

### Post by Kateikyoushi on 2007-03-11
Ubuntu is using a different filesystem than windows so you have to remove that partition and create at least 2 new ones. One for the system / and one for swap.
Swap should be smaller 1GB will do, you can make / take up the rest.
swap partition type should be swap and / should be ext3.

Take a look at this dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

