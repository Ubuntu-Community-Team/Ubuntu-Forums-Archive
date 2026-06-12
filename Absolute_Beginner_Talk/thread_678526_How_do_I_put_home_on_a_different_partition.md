---
title: "How do I put /home on a different partition?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by EleFlameMax on 2008-01-26
I'm new to partitioning hardisks, and I want to put my /home drive onto a different part of my hardisk so that I can experiment with different Distributions. I heard about this in an article, but the article was way too advanced for me. Aren't I bright? :KS 

Anyways, help would really be appreciated.

---

### Post by LaRoza on 2008-01-26
I recommend keeping home on the same partition as root so the distributions don't mess with the other configurations.

---

### Post by EleFlameMax on 2008-01-26
But how do I partition hard disks?

---

### Post by click4851 on 2008-01-26
I used a howto from [www.psychocats.net](www.psychocats.net) on creating a seperate /home partition, and yes its worth it. Good luck, for just partitioning I have had good luck with Gparted, use the gparted LiveCD if you want to partition on the same drive as your OS.

---

### Post by rosegarden78 on 2008-01-26
> **EleFlameMax said:**
> But how do I partition hard disks?

LaRoza is right, but partitioning happens in Step 4 of Ubuntu installation.  If you use guided partitioning, select Largest Contiguous Free Space.  If you choose custom you'll need to split your Primary partition into Two Primary partitions.  You can create 3 partitions as well but, like LaRoza said, let Ubuntu handle /home for you because of the settings that are stored there.  Make sure at least one partition you make is set for "/" and another (roughly 2.5x your memory) as a swap file.

Since you'll have 2 partitions, files you keep on one won't affect the other when you reinstall the OS.  With a 3rd partition you can install both operating system and  those files are safe.

---

### Post by LaRoza on 2008-01-26
512 MB of Swap is enough. The 2x recommendation is outdated but sticks around.

---

### Post by rosegarden78 on 2008-01-26
Yesterday I suggested someone physically move the /home directory to another partition after installing Ubuntu, then, use a symlink to point /home to the new location.  Any chance this would work because I use a symlink to point WINE to Common Files on my sda1 partition and it works.

---

### Post by bwtranch on 2008-01-26
no I recommend making a separate /boot dir if you are going to be playing around with different distros. Part it off as hda/ext2 or 3 /boot and you only have to give it 512 MB. Then, you can assign filesystems to the rest. 

Now what you put in the /boot is the key and you should make sure that you have the kernal qualifiers that you want to use in there. Look to the Gentoo web site. They have all the instructions. These people on this forum don't know what I am talking about.

---

### Post by rosegarden78 on 2008-01-26
Where is the link to the Gentoo web site please?  The symlink to the Common Files does work for WINE.  I haven't and probably won't experiment with /home directory though.

---

### Post by LaRoza on 2008-01-26
> **bwtranch said:**
> These people on this forum don't know what I am talking about.

Nice. You just insulted near to half a million people.

There are advanced users (that use various OS's, including Gentoo) and beginners on this forum. However, such elitist attitudes have no place on any forum.

[quote="UbuntuForums Code of Conduct"]
1. Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.
[/quote]

---

### Post by LaRoza on 2008-01-26
> **rosegarden78 said:**
> Where is the link to the Gentoo web site please?  The symlink to the Common Files does work for WINE.  I haven't and probably won't experiment with /home directory though.

[http://www.gentoo.org/](http://www.gentoo.org/)

---

