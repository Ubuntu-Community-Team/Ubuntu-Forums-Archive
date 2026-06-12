---
title: "need help partitioning"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bfolk on 2007-05-29
i need helppp i have three options one is sev/sda with no size beside it i believe the other is close to the same like sev/sda/ntfs /... which has 80 gigs and the last is free space w/ 8 megs..i need to edit the 80 gig partition to where i can set aside 5gb or so for ubuntu; however, its only letting me change themount point, and set as options....when i click edit the sev/sda it tells me that i will remove all current partitions, and i cant have that bc i run it.xp, and obviously free space doesnt have enough room to run ubuntu, but it does give me the correct options that i need to edit it ... so basically i need to see the edit options menu that i get w/ free space i need to see that with my 80 gig partition...and i d k y im not?? plsss helpp!!!

ps on my browser it says feisty fawn does that mean i have feisty fawn edlition? if so can i still use beryl package?

---

### Post by overdrank on 2007-05-29
> **bfolk said:**
> i need helppp i have three options one is sev/sda with no size beside it i believe the other is close to the same like sev/sda/ntfs /... which has 80 gigs and the last is free space w/ 8 megs..i need to edit the 80 gig partition to where i can set aside 5gb or so for ubuntu; however, its only letting me change themount point, and set as options....when i click edit the sev/sda it tells me that i will remove all current partitions, and i cant have that bc i run it.xp, and obviously free space doesnt have enough room to run ubuntu, but it does give me the correct options that i need to edit it ... so basically i need to see the edit options menu that i get w/ free space i need to see that with my 80 gig partition...and i d k y im not?? plsss helpp!!!

ps on my browser it says feisty fawn does that mean i have feisty fawn edlition? if so can i still use beryl package?

Hi I dont use feisty but let me give it a try. Under system,administration, do you see gparted. If so you can resize the windows partition there. I believe it will give you the options to resize that partition. And yes you can use beryl if your video card supports it. Good luck!:popcorn:

---

### Post by Gagle on 2007-05-29
You can resize your NTFS partition  using GParted.  It is by default integrated into the Feisty Live CD. 

In Windows, defrag your NTFS drive first, then start the installation by rebooting the Live CD.  A "install" Icon should be on the Desktop as soon as Ubuntu loads.  Double-Click on it.

From there, you will be prompted for easy configurations until you reach the critical point of partitioning your hard-drive.  

The GParted version in this install is really nice so you don't need to do anything.  Just need to resize your NTFS partition.  This is done by selecting Guided - Resize and then selecting the amount (%) of the NTFS hdd you want to keep. (i.e. : Selecting 95 % means your  NTFS hdd will 95% of what it was. )

Take a look (hope this link works...)   :  [http://img379.imageshack.us/my.php?image=feistydual06rw5.png](http://img379.imageshack.us/my.php?image=feistydual06rw5.png)

Then, the freed space will be used automatically to partition (root and swap) and install Feisty Fawn.

Good luck with Beryl .  I hope you have a "recent" NVidia card.  Unless you wil need to do some tweaking.

EDIT : Beryl can only be used once Ubuntu is installed, not on  the live CD.  Also note that once installed , the default Desktop Efects in Feisty are  Compiz and not Beryl.  They will soon remerge as a whole but for now I advice you to use Beryl.

---

