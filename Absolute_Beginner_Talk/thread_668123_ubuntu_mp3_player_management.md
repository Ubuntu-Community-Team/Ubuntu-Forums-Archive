---
title: "ubuntu mp3 player management"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by r3bol on 2008-01-15
I have an mp3 player that sometimes locks its content and i have to boot into Windows :mad: to delete/reformat the drive's contents. 
Can someone recommend a gui app that will enable me to reformat my drive in Linux if this happens again?
Thanks.

---

### Post by fiddledd on 2008-01-15
Don't know about the MP3 Player but you can format/partition Drives  wth GParted. If it's not in the System Admin menu (Partion manager or something like that) it will be available via synaptic or "apt-get installl gparted".

---

### Post by erginemr on 2008-01-15
> **r3bol said:**
> I have an mp3 player that sometimes locks its content and i have to boot into Windows :mad: to delete/reformat the drive's contents. 
Can someone recommend a gui app that will enable me to reformat my drive in Linux if this happens again?
Thanks.

Be careful with that! Not sure, but a formatting may unintentionally wipe off the boot system files (mp3 player menu) too from your player, rendering it unusable in the end.

There are tools under Windows to grab and backup the firmware part of your player...

---

### Post by r3bol on 2008-01-15
> **erginemr said:**
> Be careful with that! Not sure, but a formatting may unintentionally wipe off the boot system files (mp3 player menu) too from your player, rendering it unusable in the end.

There are tools under Windows to grab and backup the firmware part of your player...
;)I've done it loads of times so i think the firmware is somewhere else (?) What is important is that I use a FAT16 partitioning system when formating. 
...
Thanks for the gparted advice. I'll google it before trying it as I thought it was just for hard drives.

---

