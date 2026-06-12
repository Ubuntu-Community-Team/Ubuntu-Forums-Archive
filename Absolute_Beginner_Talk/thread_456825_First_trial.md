---
title: "First trial"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by peterburd on 2007-05-28
Hello, pretty much a newbie, but I managed to install Ubuntu on my laptop.  When I tried to do it on my main PC I ran into a couple of stupid problems.

I have a 40gb disc where Windows  XP resides and two 200gb drives where I store stuff.  All of these drives have plenty of spare room.  

I want to install Ubuntu on that 40gb drive, sharing it with XP.

But the Ubuntu installation wanted to install on one of the 200gb drives, probably because it has the most free space.  

I know I can use the manual partition option, but I'm not comfortable with that.  It's not intuitive to say the least. 

Peter

---

### Post by Ek0nomik on 2007-05-28
Just manually edit the partition table.  It's really easy, trust me.  :)

Firstly, make sure you have all your data backed up.  Never can be too safe.  :)

Next, boot into Ubuntu Live CD and fire up the Installation process.

Choose to manually edit your partition table.

I don't know how much space of Windows XP you need, so that is completely up to you.  Everyone is different as to how much space for each O/S they want to allocate.  What you need to do though, is create an EXT3 partition and a SWAP partition.  EXT3 is where all your Linux directories will reside.  SWAP acts as a safeguard for if you run out of RAM.  I would make your SWAP 1.5 or 2 times the amount of RAM you have.

Then, just continue on with the installation process and you can boot into Ubuntu.

If you have more questions let me know.  Trust me though, the manual edit is really user friendly.

---

### Post by peterburd on 2007-05-28
I tried the manual edit on my laptop.  As I said, it's not intuitive.  I'll study a little more.

The question remains: If Ubuntu can do an "easy" partition on a disc drive, why can't we chose the damn drive??

---

### Post by stalkingwolf on 2007-05-28
It may be as simple as unplugging your other drives during installation.  How is your win drive partitioned?
You might be able to use the " use free space " option ( defrag first) which will automatically configure free
space( as I recall)  to the required / and swap partitions needed for install.

---

### Post by louieb on 2007-05-28
The version of GParted on the live CD is as easy as it gets. But to bake a cherry pie you have to know how to use a oven. First find out a little bit about cherry's [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")  then find the instructions for the oven [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

BTW: If you don't back up your data first I hope you don't regret it. And since you have to shrink you XP partition, I'm with stalkingwolf : **defrag first  **

---

### Post by peterburd on 2007-05-28
Thanks for the advice.  Do to a series of misadventures I had installed Ubuntu twice (the grub was getting pretty crowded), then did gparting to get rid of one of them, but I apparently don't know "how to use an oven" and grub refused to work, not allowing me to boot at all!  So I futzed around with another installation.  I still think the manual partition option isn't very intuitive, but I managed not to blow anything up this time, and I can dual boot again.  

Of course my computer technique is "hit buttons at random" so I take the blame.

---

### Post by Ek0nomik on 2007-05-28
peterbud:  What's your question about the manual edit?  We can explain it to you if there is something specific you don't understand.

---

