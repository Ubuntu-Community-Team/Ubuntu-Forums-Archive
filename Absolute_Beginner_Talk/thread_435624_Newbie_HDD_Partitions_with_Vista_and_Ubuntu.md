---
title: "Newbie HDD Partitions with Vista and Ubuntu"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by babyman1737 on 2007-05-07
Vista Ultimate came installed on my new laptop. I want to make sure it is not deleted in the process of installing Ubuntu. GParted looks like this:
  FILE  ............         PartitionSystem  .....  Used .......    Unused  .......Flags
/dev/sda1.........fat16..............7.05MiB.......47.83MiB......
/dev/sda2.........ntfs................4.20GiB.......5.8GiB........
/dev/sda3.........ntfs................18.67GiB.....43.80GiB.....boot
/dev/sda4.........extended.........---..............---................lba
    unallocated...unallocated.....---...............---...............
    /dev/sda5.....fat16..............757.89MiB...1.26GiB.......

Does anyone have any recommendations how I can split up my partitions to make a space for Ubuntu? It's a 80GB HDD as you can tell from GParted, and I would rather not mess up my Vista partition. Are there any simple solutions for editing my partitions? Google didn't do me too much good. Thanks for any help.

---

### Post by LaRoza on 2007-05-07
Do not use GParted to alter Vista partitions, use Vista's own tool. I hear this problem has been fixed with the newest version, but I wouldn't try it.

You can search the forum for Vista dual boot issues. (I overwrote Vista, on purpose, and never dual booted it, so I do not feel qualified to answer)

---

### Post by Wiebelhaus on 2007-05-07
the easiest way to do it , is to have vista installed on a master drive , install a secondary HDD as a slave then run the ubuntu installer and point ubuntu in the direction of the secondary drive , ubuntu then does all the work , no worries.

---

### Post by antoz on 2007-05-07
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/) tutorial for dual boot including vista
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

A few good links

---

### Post by babyman1737 on 2007-05-07
sx66gns: The problem with installing on two different hard drives is that my computer is a laptop, and does not have an extra hard drive or space for it.
antoz: Thank you for the websites, I have already read through a couple of them through my google search. They either dual boot with XP (Vista is different I hear), and the Vista guide assumes you haven't installed Vista yet, and you do a custom install to break up the partitions before you install Vista.

Any other suggestions on how to help me dual boot if Vista already came installed from the factory and I don't want to overwrite it? Thanks.

---

