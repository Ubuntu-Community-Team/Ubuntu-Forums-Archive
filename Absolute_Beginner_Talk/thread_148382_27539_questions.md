---
title: "27539 questions"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2006-03-22
but i'll start with just one...everything i read says i can do win xp and ubuntu...however all tutorials i have seen tell you how to install a NEW ver of win xp...hey, i already have it as sole partition of an 80gb drive. what i want to do is take partition magic 8 and resize my freespace, and format it as ext3 ( because i'm told that is what linux uses). then, i am hoping that i can use the linux installer to create those 319 other partitions :-\. btw, are all those partitions really needed? or can i use just 1, like i do or windblows. to keep the peae, i am willing to use the /,swap,home... any advice is appreciated, aloha

---

### Post by gabruo on 2006-03-22
You should only have to resize your xp partition and simply install ubuntu into the empty portion.  The install dialog on the cd/ISO should take care of the rest including the reformating for ext3.  Good luck with partition magic make sure to backup anything of value.

---

### Post by darf681 on 2006-03-22
Is there a utility in the install program that will allow folks to resize a partition?  That would be a nice addition if it isn't already in there.  Would have to defrag the windows partition first though..

Which you probably want to do before you use Partition Magic to resize your windows partition anyways  (makes it faster and way more reliable when resizing).

If Breezy doesn't already have this feature, will Dapper?

---

### Post by KansasJoe on 2006-03-22
You'll need one partition for ubuntu (ext3) and one partition for swap space (swap) and of course your windows partition which you will just take the space from...you may want to make one for /home but that's up to you...remember when you get past 4 primarys you'll need to make one of those an extended and then you can have as many logicals as you want....you don't need to use partition magic because when you install you'll have a chance to do the partitioning there...i would actually suggest ubuntu's partitioner because it does it very quick whereas partition magic takes forever to do the partitioning once you reboot into windows....partition magic is good for when you have lost hard drive space and you need to get it back (saved me once before)

---

### Post by confused57 on 2006-03-22
I'm just a newbie also and I haven't done the dual-booting thing, but I suggest you do a search for dual-booting(especially in the thread titles), which should show threads linking to Hermanzone(excellent tutorial for dual-booting).  From what I've read it's probably best not to use Partition-Magic, but just defrag your 
WinXP a couple of times.  The Ubuntu install CD gives you the option to resize your WinXP partition, and free up the remaining space for Ubuntu.  I'm sure some of the experts will give you some practical advice, but thought I'd give a heads-up.

---

### Post by mcduck on 2006-03-22
Thei nstaller can resize windows partitons for you. Just ran defrag in safe mode first, and you should be fine. :)

Here's link to the dualboot guide confused57 mentioned: [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

