---
title: "Questions from a Newbie"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by eads1234 on 2005-06-29
I just received my UBUNTU CDs today.

I have a WinXP(SP2) system, but I want to create a dual boot system. I know NOTHING about UBUNTU, but I've had it with Microsoft.

Some info:

My PC has the latest Win XP(SP2) OS.

My primary drive (Drive "C") is an 80GB HD. Currently, I'm only using about 30 GBs.

I also have an external Maxtor 200 GB HD attached for backup purposes. This external is a hot swapable disk so it is only on when I want it around for backup purposes (Retrospect).

MY QUESTIONS ARE:
1. Do I need a partitioning program such as Partition Magic to properly accomplish the UBUNTU installation?
2. Should/Will UBUNTU be installed (install itself) on my primary drive or should/will it be on the external drive. 
3. Can I assume (uh-oh!) that the necessary partition(s) for UBUNTU is/are created by the "Install" program on the UBUNTU CD -- thus negating the need for a partitioning program?
4. How long does the installation take given average everthing (in general)?

I'll be back later this evening, and I thank you very, very much for any help of any kind!!

...RW

---

### Post by poofyhairguy on 2005-06-29
First let me say welcome. Read this and you will be on the road to freedom:

[http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/](http://www.tipmonkies.com/2005/06/23/linux-filesystems-and-partitioning-a-primer/)

You don't have to read all of it, but it has the best info.

[QUOTE=eads1234]I just received my UBUNTU CDs today.

I have a WinXP(SP2) system, but I want to create a dual boot system. I know NOTHING about UBUNTU, but I've had it with Microsoft.

Some info:

My PC has the latest Win XP(SP2) OS.

My primary drive (Drive "C") is an 80GB HD. Currently, I'm only using about 30 GBs.

I also have an external Maxtor 200 GB HD attached for backup purposes. This external is a hot swapable disk so it is only on when I want it around for backup purposes (Retrospect).

MY QUESTIONS ARE:
1. Do I need a partitioning program such as Partition Magic to properly accomplish the UBUNTU installation?[/QUOTE]

Well. Partition Magic does do a really good job. It will take that one big NTFS parition, and rip it in half. It will also convert you Maxtor drive into fat32 (Linux can only read ntfs, not write to it. But it can do anything to fat32.) If you Maxtor is already fat32...and you don't want to buy parition magic....hmmm...let me think.

Ubuntu's installer is the most primative part. I don't think it can split a NTFS parition. But I know a linux that can-Mandrake. First you must defragment the main drive in XP. Then:

Download the first CD:

[http://ftp.belnet.be/linux/mandrake-iso/10.2/i586/Mandriva-Linux-2005-Limited-Edition-Download-CD1.i586.iso](http://ftp.belnet.be/linux/mandrake-iso/10.2/i586/Mandriva-Linux-2005-Limited-Edition-Download-CD1.i586.iso)

Burn it to an ISO file and both mandrake and Ubuntu:

[https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28iso%29)

Go through it to the point that you do the partitioner. Use the mandrake paritioner to split the NFTS drive. Then when it asks for a second CD, just turn it off. Put in the Ubuntu cd:

[http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso](http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso)

And install Ubuntu.

Of course the partition magic way is easier.

> 2. Should/Will UBUNTU be installed (install itself) on my primary drive or should/will it be on the external drive. 

the primary, in its own parition, would be better.

> 3. Can I assume (uh-oh!) that the necessary partition(s) for UBUNTU is/are created by the "Install" program on the UBUNTU CD -- thus negating the need for a partitioning program?

Look above for explination on that. I will say that during the install, the default setting might want to write over your Window's parition, so don't let it write changes to disk when it askes. When you say no (on the next screen) chose and hit enter on the parition you made and it will install to that. It will automatically set up Windows so you can use it if you need to.

> 4. How long does the installation take given average everthing (in general)?


It takes me an hour on my 400mhz celeron, but only 20 minutes on my new P4.

Ask anything else you need. I'm moving this to a better forum if you don't mind.

---

### Post by ante0 on 2005-06-29
Hello, 

1st qt: Ubuntu installation cd has a builtin partionprogram.
2nd qt: As you partion the primary drive you should install it on the primary drive. i donno if this is the best choice, cuz im no expert. 

3rd: see answer 1 =P
4th: I guess the time depends on your computer, took like 30-60 mins for me to install.

Have fun, :)

And if you havnt tried ubuntu before you should use the Live cd that came with the install cd =)

---

### Post by ante0 on 2005-06-29
damn, i was too late, oh well...

Use the other guys post instead =)

---

### Post by eads1234 on 2005-06-29
Thanks anyway.

---

### Post by UbuWu on 2005-06-29
[QUOTE=poofyhairguy]
Ubuntu's installer is the most primative part. I don't think it can split a NTFS parition. [/QUOTE]
I think it can. I think it did that for me :-)

---

### Post by Scoodaddy on 2005-06-29
Download Bootit NG from [www.terabyteunlimited.com](www.terabyteunlimited.com).  Uncrippled evaluation version, can run off floppy, can do anything you want to your partitions.  Great program.

---

### Post by eads1234 on 2005-06-29
You've given me lots to work with/on. Thank you. I'm sure I'll have other questions, but right now I seem to have a lot of digesting to do. Again, Thanks!

---

