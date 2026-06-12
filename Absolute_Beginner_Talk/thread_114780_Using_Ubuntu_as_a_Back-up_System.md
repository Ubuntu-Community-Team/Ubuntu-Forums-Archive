---
title: "Using Ubuntu as a Back-up System?"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by olieviya on 2006-01-09
Would you recommend using Ubuntu as a back-up system, like in the very very frequent event of winXP falling apart?

And of course saving some important files in Ubuntu as well as on the HDD winXP will be on?

---

### Post by olieviya on 2006-01-09
*or partition

---

### Post by estel on 2006-01-09
Errmmm... I wouldn't recommend it over a zip drive or other external storage.

---

### Post by Jimmey on 2006-01-09
Yeah - Well, at least I can't think of a reason why not.

I'd advise having the Ubuntu partition being a FAT32, that way you can easily exchange files between the two operating systems.

Just to add, I've a dual boot Windows XP with Ubuntu, and I use the Windows partition as my "Back-up" - I keep it there incase I break something ( because I'm new ), incase I need Windows for some special piece of software, and because it's too expensive to just delete. You should try that :D

---

### Post by KingBahamut on 2006-01-09
Are you wanting to create images of Drives or just sets of data?

---

### Post by rooster on 2006-01-09
[QUOTE=olieviya]Would you recommend using Ubuntu as a back-up system, like in the very very frequent event of winXP falling apart?

And of course saving some important files in Ubuntu as well as on the HDD winXP will be on?[/QUOTE]
Then you have still the problem of only one HDD failing. Maybe the journalling filesystem ext3 is safer than FAT32 (and NTFS???), but you still have all the eggs in one basket.

But you can use ubuntu to save the data from a Windows-machine (or partition on the same disk) reguarly to a CD (via cron-job and "dd" or archiving software) or other device. [COLOR="Silver"]But this is - prinicipially - possible unter Windows, too.[/COLOR]

So you have to decide for yourself if you want real backups or a little more safety on another HDD or a little less risk on the same HDD...

Maybe you can just write why you are thinking about a backup (what kind of data, value for you, size, etc.).

Rooster

---

### Post by olieviya on 2006-01-09
What I want basically is a secure, virus-free, area on my pc that will work in emergencies. I need text, image, video etc files to be saved on that part or the pc and be available even if the winXP fails. I thought that perhaps using Ubuntu for this is a better idea, then just having a back-up disk with all the files on because it will also provide a way to access the files without needing to have to fix Windows before being able to access them.

I don't now how much of a good idea this is and that's why I'd like to hear your opinions.

---

### Post by KingBahamut on 2006-01-09
Sounds like data replication. Just copy the data from your windows system to your ubuntu system. 

Of course alternately, you could just get used to using your Linux partition, and then never touch your windows partition ever again, but thats another story entirely.

---

### Post by olieviya on 2006-01-10
It's not really about getting used to Linux it's about wanting to use winXP on a daily basis because it's part of my course. I don't know what a good plan is to backup data that means having it readily accessible without having to use windows at all, I thought that might have been a good one.

---

### Post by Tuf on 2006-01-10
Putting it on removable media will still give you access to from either OS and is of course safer than having it on a hard disk.

---

