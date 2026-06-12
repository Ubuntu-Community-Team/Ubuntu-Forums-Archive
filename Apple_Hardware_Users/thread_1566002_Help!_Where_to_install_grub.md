---
title: "Help! Where to install grub"
date: 2010-09-01
forum: Apple Hardware Users
---

### Post by airtower on 2010-09-01
I'm in the middle of an install on my new MacPro 3,1...This is a preowned system and has some additional drives installed. Installing GRUB to /dev/sda3 isn't even an option for me, nor do I think it would apply to me. I've installed rEFIt and booted from the liveCD without problems.

The system has three drives, two are not being used. The boot drive is /dev/sdb and the GRUB installer says /dev/sdb2 has MAC OS X. Other options on this drive are:

/dev/sdb
/dev/sdb1
/dev/sdb-1 (never seen this before)
/dev/sdb2

The documentation only states to put it on /dev/sda3 but gives no reason as to why it should go there, so I'm stumped where it should go for me.

thanks in advance!

---

### Post by dngfng on 2010-09-02
Hi,
its best to just put grub on the same partition as your Linux installation (even so it doesn't make a difference if you put it on any other partition, its just cleaner).

rEFIt will find all bootloaders on your drive no matter where they are installed.

sdb3 - is referring to a potential 3 partition, have you partitioned the drives at all?. Have a look at my Dual/Triple booting guide in my Signature - that should have most things covered.

<ramble>
I had the case that on my first Ubunut install I installed to the primary partition and on the second I followed the guide Triple boot guide witch state to put it on the same partition as the Linux installation.

I ended up with double Linux entries - it was not to much of a problem to remove the duplicate grub and fix it. 
</ramble>

Back to the point just install it on the same parition.

Remember to also have a swap partition in place.

---

### Post by garvinrick4 on 2010-09-02
> **airtower said:**
> I'm in the middle of an install on my new MacPro 3,1...This is a preowned system and has some additional drives installed. Installing GRUB to /dev/sda3 isn't even an option for me, nor do I think it would apply to me. I've installed rEFIt and booted from the liveCD without problems.

The system has three drives, two are not being used. The boot drive is /dev/sdb and the GRUB installer says /dev/sdb2 has MAC OS X. Other options on this drive are:

/dev/sdb
/dev/sdb1
/dev/sdb-1 (never seen this before)
/dev/sdb2

The documentation only states to put it on /dev/sda3 but gives no reason as to why it should go there, so I'm stumped where it should go for me.

thanks in advance!
Always install grub in sdb not sdb1 or sdb2 but sdb

---

### Post by dngfng on 2010-09-02
> **garvinrick4 said:**
> Always install grub in sdb not sdb1 or sdb2 but sdb

Hi,

I am just wondering - I know on good old PC's you defiantly should install the boot loader to the primary partition. 

But at least my (rather limited) experience with Intel Macs following a guide on Triple booting with rEFIt actually advised on installing the grub boot loader to the same partition as Linux. rEFIt doesn't seam to mind where the boot loader sits - or is there some fundamental misunderstanding on my part?

---

### Post by garvinrick4 on 2010-09-02
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by airtower on 2010-09-02
I ended up rolling the dice and chose one of the available options... can't recall which one (ok, I had had a few brews) but it completely hosed it up. I got to grub and the Ubuntu boot screen came up, but it hung. Restarted and then it would continually hang at the rEFIt tux logo. Bootcamp wouldn't let me clear the partition without a recovery disk, and gParted complained about GPT. Running gParted as su finally let me start from scratch.
 
It became clear to me that in the install guide they were prompting me to install GRUB to the linux partition, but it would not allow me to do this since I was installing to the largest continous free space and that partition had not yet been created. So I manually configured my partition tables and then set GRUB to load on /dev/sdb3. This worked out better anyway, as I did not want to run a swap partition and installing to the largest continuous free space defaulted to a rediculous 25gb swap partition.
 
Works like a charm now, expect that after selecting Linux in rEFIt, I then get a GRUB prompt where I have Ubuntu, recovery, memtest and OS X to choose from. I'll need to toy with that so there's no prompt, but I can figure that out.
 
It was a headache, and reminded me why I hate dual booting lol

---

### Post by dngfng on 2010-09-02
> **airtower said:**
> 
Works like a charm now, expect that after selecting Linux in rEFIt, I then get a GRUB prompt where I have Ubuntu, recovery, memtest and OS X to choose from. I'll need to toy with that so there's no prompt, but I can figure that out.
 
It was a headache, and reminded me why I hate dual booting lol

This has been discussed before - it boils down to this.

-shorten Grub timeout to 1/0 Seconds (depending on weather you want to be able to utilise Grub at all by quickly holding down an arrow key or not) 

-remove unwanted entries from Grub bootloader.

you can do all this in the grub settings file.

```

sudo gedit /boot/grub/grub.cfg

```

---

