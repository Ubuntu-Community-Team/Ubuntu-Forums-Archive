---
title: "Install Ubuntu when WinXP is already present"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by zelab on 2006-02-01
Is it possible? I want to leave WinXP present while being able to choose wether I want to run Ubuntu or WinXP at startup. Also, I only have one harddrive. Will this be a problem? I cannot afford to lose anything in the WinXP part of the drive, and I still have a large amount of space on the drive.

So... can I install Ubuntu without losing any of the data that is currently on the harddrive?

---

### Post by advoss on 2006-02-01
Yes it is possible.  It will involve reparitition your hard drive which can be done without loosing data.  I only know how to use Partition Magic but im sure there are free open source options ot accomplish this.  If you happen to have partition magic i can post back with instructions for using that otherwise i will let somone else reply with a good open source option.

Just somthing to remember with dual booting with Win XP, chances are XP is formated as NTFS so you will only be able to read files on in from Ubuntu and wont be able to write to that partition.  From Windows you can install drivers that will let you read and write to Linux partitions but they aren't there by default.

---

### Post by Qrk on 2006-02-01
It is very possible... in fact 80% of us here have the same setup.

Just defrag and clean your windows drive, boot in the install cd and go. When you get to the "partitioning" stage of the install, select to resize your /dev/hda1 partition.

---

### Post by RavenOfOdin on 2006-02-01
[QUOTE=advoss]Yes it is possible.  It will involve reparitition your hard drive which can be done without loosing data.  I only know how to use Partition Magic but im sure there are free open source options ot accomplish this.[/QUOTE]

BootIt NG (check my signature for link) does exactly that. When my 69.4 GiB NTFS partition wouldn't resize and no free space was detected, even though more than two thirds of that drive was free space, it re-partitioned without any loss of data or extremely long wait.

But as a safety rule, and before that, I defragged twice in my main XP account and once in safe mode under Administrator. 

I hope that suggestion will help you.

---

### Post by zelab on 2006-02-01
Okay... so it is possible. But how do I make sure I dont accidently partition off a bunch of my WinXP data? I dont know much about defragmenting or partitioning, and dont want to brick my PC.

@ advoss: Yes, it is NTFS.

---

### Post by Ozitraveller on 2006-02-01
You might find this useful too. 
 
Ubuntu Dual Boot:
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by AndyCooll on 2006-02-01
[QUOTE=zelab]Okay... so it is possible. But how do I make sure I dont accidently partition off a bunch of my WinXP data? I dont know much about defragmenting or partitioning, and dont want to brick my PC.

@ advoss: Yes, it is NTFS.[/QUOTE]

There can be no absolute 100% guarantees unfortunately. 

However if you follow qrk's advice and defrag your WinXP drive first it is highly unlikely you'll make a mess of your WinXP drive. The partition tool when installing Ubuntu moves files etc for you when creating your new partition. This pc I'm typing this to you on is a dual boot pc set up in exactly the way qrk mentioned. I halved the size of the XP partition, yet it can still boot to XP fine and dandy.

:cool:

---

