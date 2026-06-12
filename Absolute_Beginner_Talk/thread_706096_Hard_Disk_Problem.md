---
title: "Hard Disk Problem"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Dieselguts on 2008-02-24
when installing ubuntu, i got to the partition section with my friend and he noticed that it sayed SCSI at the beginning of my hard drive. He sayed that i would not be able to install ubuntu with windows as well so he suggested installing ubuntu in Virtual box. now, this takes absolutely ages and as i pressed install on the last page, it got to 15% and the dvd drive stopped whirring and the whole thing just froze.

i need some help from someone who might know what to do next.
Thanks

---

### Post by zvacet on 2008-02-24
> this takes absolutely ages

If everything else is O.K. it is ram.Virtual machine can not use all ram you have.One part of ram goes to main OS and other you give to virtual machine.That is the reason why is slow.

---

### Post by angrboda on 2008-02-24
Hi,

if you intend to use ubuntu frequently, running it in a vm might be a bit slow anyway. I don't see, why you should not be able to make a regular install. It should not matter whether your hard-drive is scsi. You should be able to resize your windows partition and install Ubuntu in the free disk space thus created. Be sure to backup your data, however. Although resizing is quite save these days, there still is the risk of data loss.

---

### Post by angrboda on 2008-02-24
by the way: are you using the live-cd? That might aggravate the memory problem further, since the live system has to be kept in ram... Should you absolutely prefer a vm it might be wise to use the alternate-install-cd rather than the live-cd...

---

### Post by sandysandy on 2008-02-24
> **Dieselguts said:**
> when installing ubuntu, i got to the partition section with my friend and he noticed that it sayed SCSI at the beginning of my hard drive. He sayed that i would not be able to install ubuntu with windows as well so he suggested installing ubuntu in Virtual box. now, this takes absolutely ages and as i pressed install on the last page, it got to 15% and the dvd drive stopped whirring and the whole thing just froze.

i need some help from someone who might know what to do next.
Thanks

first of all how many partitions do u have. 
if u have an extra partition just go ahead with the normal install process and choose the selected partition during install process and let ubuntu format it to ext 3 (linux requirement) and ubunru should install ok on it. during install a swap partition will also be created.

if u do not have an extra partition, ubuntu can still resize ur existing windows partition and install on the free space thus generated. alternatively there is an utility called GParted (available on internet, google it) which when burned onto CD as an ISO image can be booted into. This allows you to resize ur partitions and create desired partitions on the free space thus generated.

here's a nice link to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

just remember to BACKUP important data.

regards

---

