---
title: "[SOLVED] Having a senior moment here folks,"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-10-26
For the life of me I cannot remember how to reduce Fat to NTFS ! A diet won't do it, so I guess I need a memory booster, please.

Much appreciation extended,

Jon

---

### Post by qpieus on 2007-10-26
I don't understand your question. Do you mean convert a fat32 formatted drive to an NTFS formatted drive?

---

### Post by Romin-1 on 2007-10-26
That's it. I spent too much time in windoze today and it made me giddy.

NFN. I was cleaning all the bloatware out of a new Vista PC and when done was going to switch from fat32 to NTFS. After about 2gigs of cleaning I had to get out of there. Whew!

Want to change the file format so my Gutsy PC can talk to the Vista machine with as few problems as possible.

Thank you,

Jon

---

### Post by naja on 2007-10-26
Hi
You mean reformat ur HD Partition from Fat32 to NTFS?
Just use gparted,its in the repositories so you should be able to install it with:
sudo apt-get install gparted
its a graphical tool to edit ur HD partitions - is it a frontend?-
BUT BE WARNED,you will lose all your data on the formated Partition,or maybe get your Partitiontable screwed if something goes wrong -doesnt happen often-
I hope the others can help you more
thanks

---

### Post by kelbizzle on 2007-10-26
I thought vista was NTFS?

---

### Post by spur on 2007-10-26
It shouldn't matter as Gutsy will read and write ntfs. I hve done it without a problem.
Actually I installed some fonts by copying them from windows to my gutsy fonts folder. It's magic I tell you!

---

### Post by Romin-1 on 2007-10-26
You're right about Vista. I have it installed as a dual boot with XP. Want to change the XP format so it's compatable with the other OSs.

Told you my mind was foggy.

Time for a nap,

Jon

---

### Post by qpieus on 2007-10-26
So you have XP on a fat32 partition and you want to change it to ntfs so vista and ubuntu can be compatible with it? There's no need to do that - ubuntu can read and write to fat32 and ntfs partitions and I assume vista can too (!). So there shouldn't be any need to convert the xp partition to ntfs for the sake of "compatibility". Plus, I don't think you can turn your fat32 into ntfs without trashing all the data on that partition.

---

### Post by Romin-1 on 2007-10-26
You are right qpieus,

Discovered that just a few moments ago. It would leave XP as just a memory.

Thanks for the insight guys,

Jon

---

### Post by freebird54 on 2007-10-26
Actually there is a command line program in Windows (certainly in XP) called convert for the express purpose of changin FAT32 to NTFS.  The switch you use with it escapes me right now, but should be easily found with Google or maybe even HELP CONVERT in DOS.  Microsoft,com has KnowledgeBase articles on it as well.....

It is not GUARANTEED not to disturb data - but the FAT structures remain intact until the final momentsm so your odds of unfussy success are good.

Enjoy!

---

