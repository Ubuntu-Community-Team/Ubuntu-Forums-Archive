---
title: "[SOLVED] How to dual boot Gutsy with XP"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-02-20
I have Win XP on a 160 GB desktop machine, with three partitions within XP. Using G Parted, I downsized the XP partitions and created a fourth partition formatted as ext3 for Gutsy (40 GB). But when I then boot up the Gutsy installer, it wants to take up the entire HD for Gutsy and is not giving me an option to select the partition I created for Gutsy. How can I get the Gutsy Installer CD to recognize the fact that I have made a partition for Gutsy, so I can keep my 3 XP partitions, load Gutsy in the ext3 partition and get a dual boot working?

There should be an option for "Use the largest continuous free space". But it is not coming. How can I get it to come?

---

### Post by bumanie on 2008-02-20
You may have to choose manual when you  get to the partitioning stage. When setting up linux, it is mandatory to have at least two partitions, one being / where all the main system files resifde and the second being a /swap partition. Many also choose to have /home partition so that if the file system gets corrupted (unlikely), it can be reinstalled and all documents, music etc. is safe. As you already have three partitions, you have to have logical partitions. This is generally not an issue with linux.

---

### Post by swarup on 2008-02-20
> **bumanie said:**
> You may have to choose manual when you  get to the partitioning stage. When setting up linux, it is mandatory to have at least two partitions, one being / where all the main system files resifde and the second being a /swap partition. Many also choose to have /home partition so that if the file system gets corrupted (unlikely), it can be reinstalled and all documents, music etc. is safe. As you already have three partitions, you have to have logical partitions. This is generally not an issue with linux.

But why should I have to do it manually? I have set up a dual boot with XP and Feisty many times before, and it always gives an option for "choose the largest continuous free space". The manual option is quite complex--one has to set up the swap partition etc, and I could never understand how to do all that. Why is the option not coming to choose the ext partition I've created, and get everything set up automatically? That is what I've always done before.

---

### Post by swarup on 2008-02-20
> **bumanie said:**
> You may have to choose manual when you  get to the partitioning stage. When setting up linux, it is mandatory to have at least two partitions, one being / where all the main system files resifde and the second being a /swap partition. Many also choose to have /home partition so that if the file system gets corrupted (unlikely), it can be reinstalled and all documents, music etc. is safe. As you already have three partitions, you have to have logical partitions. This is generally not an issue with linux.

I would prefer to use the "use the largest continuous free space"-- but it is not coming. If you can tell me how to get it to come, that is best. Otherwise, I would need some clear instructions on exactly how to use the "manual" option. The program at that stage is asking for some "root" partition or something to be made, and I do not understand what to do. Please help.

---

### Post by polmir on 2008-02-20
type in terminal
```
sudo fdisk -l
```
```
gedit /boot/grub/menu.lst
```
and post output of it.

---

### Post by louieb on 2008-02-20
> **swarup said:**
> But why should I have to do it manually?... 
Once you do it a time or two you'll find manual partitioning isn't hard. 

You say you have already used GParted to create an ext3 partition. so when you choose manual you will just click on that partition then choose edit. Tell it to mount it as / (root) -  and your done.  

Just my two cents: I'm don't like using the largest free space option. Thats just trusting that the installer does what you want it to do.  Heres a good link for dealing with it.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by housam on 2008-02-20
> **swarup said:**
> I would prefer to use the "use the largest continuous free space"-- but it is not coming. If you can tell me how to get it to come, that is best. Otherwise, I would need some clear instructions on exactly how to use the "manual" option. The program at that stage is asking for some "root" partition or something to be made, and I do not understand what to do. Please help.


You need at least two partitions for installing ubuntu ( root & swap)
- Use Gparted tool ( on the live CD ) to do the partitioning task.
- You can create up to only 4 primary partitions on single HDD.
-I suggest to leave the  3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3 ( 20 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / )  and the swap too..

---

### Post by swarup on 2008-02-20
> **louieb said:**
> Once you do it a time or two you'll find manual partitioning isn't hard. 

You say you have already used GParted to create an ext3 partition. so when you choose manual you will just click on that partition then choose edit. Tell it to mount it as / (root) -  and your done.  

Just my two cents: I'm don't like using the largest free space option. Thats just trusting that the installer does what you want it to do.  Heres a good link for dealing with it.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That's great. I followed your direction, and the ext3 partition is now selected as / (root). But then when I click "forward", the installer says I have not yet selected a swap partition, and that if I do not select one the installer will go on without one but it will not be efficient. So do I need now to create another partition and label it as a swap? If so, then which window do I need to make this new partition, and how do I label it as swap?

---

### Post by swarup on 2008-02-20
> **housam said:**
> You need at least two partitions for installing ubuntu ( root & swap)
- Use Gparted tool ( on the live CD ) to do the partitioning task.
- You can create up to only 4 primary partitions on single HDD.
-I suggest to leave the  3 primary partitions and make the 4th one as extended which can be devided to many logical partitions.
- You'll devide the extended partition to 2 partitions : one EXT3 ( 20 GB is a good space ) for installing ubuntu as a root partition ( / ). and the other one as a swap ( only 1 GB ).
- During the installation process when it comes to the partitioning choice choose the manual way and assign the EXT3 as a root ( / )  and the swap too..

I see. That is very helpful. I had already created the 4th partition as an ext3 partition. So should I go back into gparted and reformat this partition as an "extended" partition rather than an ext3? (Is there such an option for the partition type in gparted-- "extended"?)   --And then where will this extended partition be divided into two logical partitions, 1 ext3 and 1 swap? Does that get done in the gutsy installer, by choosing the manual way?

---

### Post by jcitguy78 on 2008-02-20
you said you have 4 total partitions, what are the other ones used for that aren't XP or Gutsy?

---

### Post by swarup on 2008-02-20
> **jcitguy78 said:**
> you said you have 4 total partitions, what are the other ones used for that aren't XP or Gutsy?

My XP itself has three partitions in it.

---

### Post by housam on 2008-02-20
> **swarup said:**
> I see. That is very helpful. I had already created the 4th partition as an ext3 partition. So should I go back into gparted and reformat this partition as an "extended" partition rather than an ext3? (Is there such an option for the partition type in gparted-- "extended"?)   --And then where will this extended partition be divided into two logical partitions, 1 ext3 and 1 swap? Does that get done in the gutsy installer, by choosing the manual way?

Yes you'll go back and reformat the 4th partition to extended one . you 'll do it all with the Gparted tool before going to installation

---

### Post by swarup on 2008-02-20
> **housam said:**
> Yes you'll go back and reformat the 4th partition to extended one . you 'll do it all with the Gparted tool before going to installation

I just went into gparted, and looking under the "formatting" options-- I do not see any option for setting it to type "extended". There are options for ext2, ext3, ntfs, fat32 etc but I do not see any option for setting it to type "extended". Where is that setting found? And then the subdivision into two logical partitions (ext3 and swap)-- that is also done in gparted? Where is the option for it? (Sorry for all the questions!)

---

### Post by jcitguy78 on 2008-02-20
> **swarup said:**
> My XP itself has three partitions in it.

Are these being used for data or just storage, if you can try to simplifiy to HD by condensing the partitions. Are you running any windows apps that might be fighting for control over the ubuntu install??

---

### Post by louieb on 2008-02-20
> **swarup said:**
> I see. That is very helpful. I had already created the 4th partition as an ext3 partition. So should I go back into gparted and reformat this partition as an "extended" partition rather than an ext3? (Is there such an option for the partition type in gparted-- "extended"?)   --And then where will this extended partition be divided into two logical partitions, 1 ext3 and 1 swap? Does that get done in the gutsy installer, by choosing the manual way?
Exactly.
What I would do using the GParted CD.
Delete the ext3 primary partition.
Create an extended partition in the now unallocated space (use all)
Create two logical partitions inside the extended partition. One about 1  GB for swap the rest ext3 for / (root)

Now back to the install:
Have to use manual again. Swap will get picked up automatically.  Will just have to do the same edit and select mount point for the / (root) partition.

---

### Post by swarup on 2008-02-20
> **jcitguy78 said:**
> Are these being used for data or just storage, if you can try to simplifiy to HD by condensing the partitions. Are you running any windows apps that might be fighting for control over the ubuntu install??

They are being used for data. Yes, I can condense the three partitions down to two. And then that will leave two partitions for Gutsy: one for the ext3, and one for the swap. But-- someone else has written that if I make the 4th partition an "extended" partition, then that can itself be divided into two logical partitions-- 1 ext3, and 1 swap. But I do not see where in gparted one can designate a partition as "extended"-- and then where the "extended" partition is in turn divided into an ext3 and a swap. Can you help?

---

### Post by swarup on 2008-02-20
> **louieb said:**
> Exactly.
What I would do using the GParted CD.
Delete the ext3 primary partition.
Create an extended partition in the now unallocated space (use all)
Create two logical partitions inside the extended partition. One about 1  GB for swap the rest ext3 for / (root)

Now back to the install:
Have to use manual again. Swap will get picked up automatically.  Will just have to do the same edit and select mount point for the / (root) partition.

Great. I see-- thank you so much. But please just tell me *where *in gparted is the option for making an *extended *partition, and then where in gparted to go to make the two *logical *partitions.

---

### Post by Arthur Archnix on 2008-02-20
It looks like it may be a bit late, but I think the reason you can't use the largest continuous free space is because you created an ext3 partition in the free space. Just delete the ext3 partition, restart the installer, and you should see the option you're looking for.

---

### Post by housam on 2008-02-20
> **swarup said:**
> I just went into gparted, and looking under the "formatting" options-- I do not see any option for setting it to type "extended". There are options for ext2, ext3, ntfs, fat32 etc but I do not see any option for setting it to type "extended". Where is that setting found? And then the subdivision into two logical partitions (ext3 and swap)-- that is also done in gparted? Where is the option for it? (Sorry for all the questions!)

As Louieb said , when you delete the ext3 partition you'll get an unallocated space and you 'll be able to create a new partition. when you choose new you'll select the extended from the format list. then you will be able to devide it to a two new partitions.

---

### Post by swarup on 2008-02-20
Ok-- I found the option for "extended partition", and I've made that. Then--and please excuse me for being so naive--but how will I then divide it into two new partitions?

---

### Post by swarup on 2008-02-20
> **Arthur Archnix said:**
> It looks like it may be a bit late, but I think the reason you can't use the largest continuous free space is because you created an ext3 partition in the free space. Just delete the ext3 partition, restart the installer, and you should see the option you're looking for.

I see-- that is great. That was my mistake. In future, I'll know how to do it. Thanks again.:)

If someone can tell me how to divide the extended partition into two logical partitions, then I think the work will be done.:)

---

### Post by housam on 2008-02-20
> **swarup said:**
> Ok-- I found the option for "extended partition", and I've made that. Then--and please excuse me for being so naive--but how will I then divide it into two new partitions?

just point to it with the courser and click new and then move the right end to the size you want for the root and leave only 1 Gb for the swap.

---

### Post by louieb on 2008-02-20
Heres a long guide to GParted.  It shows just about every thing you can do.
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by swarup on 2008-02-20
Many thanks to housam, louieb, and Arthur as well as others. You have cleared up certain long-standing questions I had about how to manage gparted and the installer. I've now got gutsy properly installed, and I don't think I'll ever have another problem with partitions and installation! (Hope I don't eat my words in the future!) Thanks again. :)

---

### Post by housam on 2008-02-21
> **swarup said:**
> Many thanks to housam, louieb, and Arthur as well as others. You have cleared up certain long-standing questions I had about how to manage gparted and the installer. I've now got gutsy properly installed, and I don't think I'll ever have another problem with partitions and installation! (Hope I don't eat my words in the future!) Thanks again. :)

Congratulations..:guitar:

---

