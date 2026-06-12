---
title: "How to dual boot...."
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by icebubba2005 on 2008-04-14
Ok so I want to have windows xp and ubuntu at the same time so I want to dual boot. I already have xp installed and now how would I go about installing ubuntu so I can select which one to run at startup? Im am a complete idiot when it comes to comps so please put this in easy terms to understand. Thanks.

---

### Post by Inxsible on 2008-04-14
Check out these links which should help you set up dual boot

[Partitioning]("http://www.psychocats.net/ubuntu/partitioning")  [Installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by bumanie on 2008-04-14
If I were you, I would download a gparted live cd and partition your drive by shrinking xp and then formatting the remainder of the drive to ext3. Then insert the live ubuntu cd and at the partitioning stage choose manual with the radio button. It is mandatory to have a / partaition and a swap partition. In addition it is useful to have a separate /home partition because than you can reinstall to / if something goes wrong and all saved data in /home will be safe. The partitioner should make it clear which is the windows partition and which is the formatted ext3 partition. To set up the new partitions click on the ext3 partition and choose edit and set / to at least 6gb , then set swap to 1-2 gb and use the remainder for /home. It's a bit daunting the first time, but is not that hard. As long as you don't touch your windows partition during the installation of ubuntu, you can try again if things muck up. You should defrag xp before you shrink the xp partition and backup anything important just in case something goes wrong (like a power failure half-way through partitioning). Hope this helps.

---

### Post by beast-usa on 2008-04-14
The easy way for me so far ..... new to Linux

I set the new LINUX hard drive as first boot device. (blank new drive)
Windows multi-boot Vista & XP drive or raid drive to 2nd boot device.

Inserted 8.04 x64 CD, told it to use all of the first drive, Ubuntu setup
it's partitions. On the first boot it asked me which did I want to boot to.
Ubuntu is the first chioce, windows vista last on the list.
Worked the same on 4 systems so far. Easy for a new to Linux person..LOL

Now I'm trying to change the location of my files so they always
save to a third drive.

---

