---
title: "Reinstallation"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Klaidas on 2006-03-17
Hello :)
I've been using ubuntu for a while, and now I would like to reintall it. 
Ya, I read the whole hermanzone page about ubuntu + ntfs (I also have it in my sig.). 
I'm dual booting with Windows XP, so the drive is already partitioned. 
As i'm simply reinstalling, I dont want to resize partition, create new ones, etc. 
My question is:
How do I skip the partitioning and move over to reinstalling?

Thanks in advance :)

---

### Post by garretjax on 2006-03-17
You don't have to partion, but you still have to set what partition you want used for what in that phase.  

Just write down what ones you need to know before you start - some you will format some you wont - if you leave /home [if it was on a seperate partition] you will keep most of your desktop settings.
/boot and / you would want to format most likely

Be verry carfuly when you write down what partitions to keep and all -- if you mix it up and can be a pain in the *** - i lost something like 14 gigs of data casue i formatted the wrong partiton to be used as /

---

### Post by meborc on 2006-03-17
you can't skipp the partitioning, cuz you have to chose where you want to install ubuntu... so you have to chose 'manually blablabla' ... then select the partition where the previous version of ubuntu is installed... click on it... chose delete partition... then delete also the swap partition... then click on the FREE SPACE and select automatically partition the free space...

the partitioner then creates swap and ext3 partitions in that free space... and installs ubuntu... that is the safest method :rolleyes:

---

### Post by Klaidas on 2006-03-17
Oh, thats an interestiong way :)
Would there be any problems with GRUB (it's on my MBR) if delete partitions and then create them again?
I myselft think not cuz it the installer reinstalls GRUB in the end. Am I right?

---

### Post by meborc on 2006-03-17
[QUOTE=Klaidas]Oh, thats an interestiong way :)
Would there be any problems with GRUB (it's on my MBR) if delete partitions and then create them again?
I myselft think not cuz it the installer reinstalls GRUB in the end. Am I right?[/QUOTE]

since the installer installs like a brand new install... it will set up grup also... so no probs... :mrgreen:

---

