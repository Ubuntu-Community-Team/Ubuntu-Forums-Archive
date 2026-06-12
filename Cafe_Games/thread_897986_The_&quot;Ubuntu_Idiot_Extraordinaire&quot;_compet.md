---
title: "The &quot;Ubuntu Idiot Extraordinaire&quot; competition"
date: 2008-08-22
forum: Cafe Games
---

### Post by knattlhuber on 2008-08-22
I just did something incredibly and embarrassingly stupid while working with Ubuntu. It would really help me to know that I'm not the only idiot in the Ubuntu world. So if you did something similarly stupid, please post your story.

Here's mine:
I got a new computer today and couldn't wait to install Ubuntu. I unplugged my keyboard, mouse and monitor from my old computer, connected them to the new one and started the installation. When I came to the screen with the partition manager, I was pleasantly surprised: The computer was supposed to have one 750 GB HD but instead there were three HDs with a total capacity of >1 TB. Coool! Without thinking twice, I created the partitions, formatted all three drives, kicked off the installation, and stepped out. Then suddenly something terrible dawned on me. I stormed back to my room and found my suspicion confirmed: The USB cable that I had thought belonged to the mouse, was actually the one from the USB hub on my old computer - which had two USB HDs connected... I had just wiped off 300GB worth of data in a heartbeat.:(

Edit: Thanks to everybody who expressed their sympathy and offered their help. Fortunately, the data on the two drives was mainly backups. Using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") (it's in the repos), I was able to recover both partitions today in no time with no data loss.
The competition for the "Ubuntu Idiot Extraordinaire" is still on, so please post your stories.

---

### Post by Glucklich on 2008-08-22
Sorry dude. You won it. The trophy is yours. There's no possible competition for that.
I'm pretty dumb but... DAMN!

---

### Post by fogster74 on 2008-08-22
Ouch....

Have you actually written anything to the external hardrive? Or just wiped the partition and formatted it? It may be possible to recover data if the latter applies..

---

### Post by Glucklich on 2008-08-22
> **fogster74 said:**
> Have you actually written anything to the external hardrive? Or just wiped the partition and formatted it? It may be possible to recover data if the latter applies..

> **knattlhuber said:**
> Without thinking twice, I created the partitions, **formatted all three drives**, kicked off the installation, and stepped out.

If you can help him, please do. He probably had his life's work on those HD's.

---

### Post by knattlhuber on 2008-08-22
> **fogster74 said:**
> Ouch....

Have you actually written anything to the external hardrive? Or just wiped the partition and formatted it? It may be possible to recover data if the latter applies..

No, I haven't written anything to these drives yet, just formatted them. Luckily, the data aren't superimportant (but still worth recovering).

---

### Post by Oldsoldier2003 on 2008-08-23
I once installed Windows on a Ubuntu system... I thought it would be nice to dual boot.

---

### Post by fogster74 on 2008-08-23
> **knattlhuber said:**
> No, I haven't written anything to these drives yet, just formatted them. Luckily, the data aren't superimportant (but still worth recovering).

There could be a way out... formatting a drive does nothing at all, part from mark the areas as available for writing. The data is not destroyed - it's still there. However, if you've deleted the partition table and/or changed the drive (e.g. changed a 100GB NTFS-formatted drive to 2 x 50GB EXT3 drives) it becomes a lot more... challenging

Can you explain exactly what you've done to the 'data' partition - have you changed the partition itself, changed the file system etc?

I'm no expert but I'd be delighted to help if I can...

---

### Post by Shippou on 2008-08-23
Cool! >1TB of HD!

Well, good luck in recovering the data... 


Anyway, data is already the plural form...

Datas....

---

### Post by stinger30au on 2008-08-23
ouch.... man i feel your pain. i hope you had back up of your data

best of luck

---

### Post by knattlhuber on 2008-08-23
> **fogster74 said:**
> There could be a way out... formatting a drive does nothing at all, part from mark the areas as available for writing. The data is not destroyed - it's still there. However, if you've deleted the partition table and/or changed the drive (e.g. changed a 100GB NTFS-formatted drive to 2 x 50GB EXT3 drives) it becomes a lot more... challenging

Can you explain exactly what you've done to the 'data' partition - have you changed the partition itself, changed the file system etc?

I'm no expert but I'd be delighted to help if I can...

Thanks for offering your support, fogster74. Much appreciated.
Now, thank goodness most of my important data were on the two IDE HDs in my computer. The stuff on these two USB HDs was mainly only backed up data from my two main HDs (pheeew...). But for my life I can't remember if there was anything else on these two drives, so I rather try to restore what I can.

Contrary to what I wrote in my original post, I didn't actually format the drives but deleted the partitions (both ext2)...

I saw that there is a free tool called [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") that might do exactly what I need. I will give that a try. Other suggestions are, of course, welcome.

---

### Post by Glucklich on 2008-08-24
How cool is that? A story with a nice, happy ending.

---

### Post by beercz on 2008-08-26
[I must come a close second at least]("http://ubuntuforums.org/showpost.php?p=1019203&postcount=45")

---

### Post by stinger30au on 2008-08-26
> **knattlhuber said:**
> Edit: Thanks to everybody who expressed their sympathy and offered their help. Fortunately, the data on the two drives was mainly backups. Using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") (it's in the repos), I was able to recover both partitions today in no time with no data loss.


awesome!!! glad you got it all back:guitar:

---

### Post by Glucklich on 2008-08-26
> **beercz said:**
> [I must come a close second at least]("http://ubuntuforums.org/showpost.php?p=1019203&postcount=45")

DAAAAAAMN! That's nasty.

---

