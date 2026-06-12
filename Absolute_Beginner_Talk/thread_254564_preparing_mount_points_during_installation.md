---
title: "preparing mount points during installation?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by latecomer on 2006-09-10
(Apologies if the info provided is a bit redundant, but it's noob-central here and I don't want to mess up my set-up :biggrin: )

I'm about to install ubuntu as a dual-boot on my HP laptop, 75GB HD, and have already done the following with the gparted livecd:
   -resized my ntfs partition down to about 55GB
   -created 3 new partitions for ubuntu, one for root, swap, and /home respectively
Now, when I run the installer from the ubuntu livecd, at step 5 I choose to 'manually edit partition' and it gives me:
   /dev/hda1  ntfs        55GiB
   /dev/hda2  ext3        5GiB
   /dev/hda3  linux-swap  1GiB
   /dev/hda4  ext3        14Gib  

then I go forward to 'prepare mount points' it defaults to:
                                  
   /media/hda1  55GiB for hda1      
   /media/hda2   5GiB for hda2          
   /swap         1GiB for hda3      
   /            14GiB for hda4      

so I change hda2 to '/' , hda3 is fine, hda4 to '/home' and I BLANK OUT both entries for hda1.
Then in step 6 it tells me:
   WARNING: This will destroy all data on any partitions you have removed 
   as well as on the partitions that are going to be formatted.
so I chicken out :confused: 
Can anyone tell me, with relative confidence :biggrin: , if leaving my 55Gib WinXP partition as a /media/hda1 mount point will affect it in any way? 
Also, is it better to reformat the /home partition as well? (I know it says it's not necessary, but I'm just wondering)
Thanking you in advance for your expert advice :grin:

---

### Post by orb9220 on 2006-09-10
It is fine just a warning and you are doing just fine. Just verify that your ntfs partition hda1 dosn't have a checked mark for reformat at the right of the page it should already be unchecked and all the others should.

---

### Post by latecomer on 2006-09-10
So do I leave it as /media/hda1 or do I blank it out in the 'prepare mount points' step? Sorry, but I'm a bit thick :biggrin: 
Thanks

---

### Post by xpod on 2006-09-10
your windows partition should already be blanked out....I.E.. NO little tick in the checkbox.
Only your new ubu partitons should have the little box ticked.

So you should have an empty top box and the three underneath(ubu) should be checked so it`s only  them that are formatted

---

### Post by latecomer on 2006-09-10
sorry to try your patience, but with blanking out I meant the entries for mount point 'media/hda1' and the one next to that (a more detailed description of the partition but I can't remember the exact phrasing). The checkbox for reformat was indeed unticked and I had no intention of ticking it :wink:
So you're saying to mount my XP partition as /media/hda1 and this WILL NOT affect it or make XP go funny (well, any funnier than it already is of course :p )  
Thanks again

---

### Post by Linux Lover on 2006-09-10
Take care while checking the ticks. I think the ticks will be put automatically if any partition needs formating, and you only have to check it. Though you can manually put a check mark or uncheck the Reformat column.

No tick in Reformat column for your Win partition.
Tick in Reformat column for your / partition
Tick in Reformat column for your swap partition
Tick in Reformat column for your /home partition.

If you ever think to unmount your Win partition from each time you boot, you can do it later too.

---

### Post by orb9220 on 2006-09-10
Linus will create a mount point for your windowsxp but that is just a link  to the hardrive so you can access stuff that is on the winxp side. It does not do anything to your xp partition.

---

