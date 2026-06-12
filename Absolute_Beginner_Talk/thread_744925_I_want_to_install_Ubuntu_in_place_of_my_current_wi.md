---
title: "I want to install Ubuntu in place of my current windows partition"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Vorteilspreis on 2008-04-04
I'm new to Ubuntu and I'd just like to know how to install Ubuntu over top of my Windows XP partition. Thanks.

BTW, how much hard drive space does Ubuntu take up?

---

### Post by joshrobinson on 2008-04-04
> **pat666rick said:**
> I'm new to Ubuntu and I'd just like to know how to install Ubuntu over top of my Windows XP partition. Thanks.

so you want windows to be gone, and the only thing on the hard-drive to be ubuntu?
theres no data your worried about losing correct? if so back that up first

when you boot the live cd, and it gets to the installer, it asks you what to do with your partitions, just click the "use entire disc" option

and windows will be gone, along with EVERYTHING on the hard-drive

---

### Post by paydaydaddy on 2008-04-04
Are you sure that you are ready to do that? Do you have other access to the internet for when you run into problems with Ubuntu? The learning curve for Ubuntu can be pretty steep, so it is a good idea to have a backup plan. Maybe dual boot. Do plenty of research before making it all or nothing for Ubuntu. My personal recommendation is install Ubuntu on a seperate disc, if possible, as a way to get started without messing up xp. Opinions will vary. Lots of help here, just make sure you keep your options open.

---

### Post by Vorteilspreis on 2008-04-04
> **joshrobinson said:**
> so you want windows to be gone, and the only thing on the hard-drive to be ubuntu?
theres no data your worried about losing correct? if so back that up first

when you boot the live cd, and it gets to the installer, it asks you what to do with your partitions, just click the "use entire disc" option

and windows will be gone, along with EVERYTHING on the hard-drive

I know about the "entire disc" option but I only want to get rid of only one of the partitions (the windows partition) that I have on my primary HD. Is there a way to do this? Or will I have to get rid of ALL of the data on the entire HD?

---

### Post by Vorteilspreis on 2008-04-04
> **paydaydaddy said:**
> Are you sure that you are ready to do that? Do you have other access to the internet for when you run into problems with Ubuntu? The learning curve for Ubuntu can be pretty steep, so it is a good idea to have a backup plan. Maybe dual boot. Do plenty of research before making it all or nothing for Ubuntu. My personal recommendation is install Ubuntu on a seperate disc, if possible, as a way to get started without messing up xp. Opinions will vary. Lots of help here, just make sure you keep your options open.

I think that I'm ready to do this... I know that there will be quite a steep learning curve with ubuntu (and linux in general) but I should eventually get the knack of it.

---

### Post by tangibleorange on 2008-04-04
oh right. no there is a stage in the installer called "manual" which will allow you to manually configure partitions for install. you can also use gparted, which is on the live cd and can be accessed from the terminal with this command:

```
gksu gparted
```

---

### Post by DarkSaga70 on 2008-04-04
when you use the live cd you can choose wich partition you install to. Just go over the windows partition.

---

### Post by scannerdarkly on 2008-04-04
so i'm going to guess that you have more then one parition.  odds are that the first partition is going to be the windows partition.  When you load the live cd and you get to the partitioning section just click on Manual config....I think that what it's called.  I'm at work so I can't confirm the name....But anyway it should be the last option on that screen.  Once you select that you'll get a screen with the different partitions that are on your drive.  Your gonna have to make the right call in selecting the correct partition.

After install and updates which i think there are about 230+ updates it should take something like 2 to 3 GB of space.

---

### Post by joshrobinson on 2008-04-04
you can use the manual option, and remove the partitions you dont want
just be sure you know the size of the partition you want to delete before you do, so that way you know its the right one

---

### Post by Vorteilspreis on 2008-04-04
Ok, I clicked on manual and I selected the partition that I wanted to use. I got this message though...

[IMG]http://i78.photobucket.com/albums/j81/pat666rick/Screenshot-1.png[/IMG]

---

### Post by joshrobinson on 2008-04-04
on the partition you want to use, click it so its highlighted
then click edit
then click format as ext3
then set the mount point as   /
just the slash

---

### Post by Vorteilspreis on 2008-04-04
> **joshrobinson said:**
> on the partition you want to use, click it so its highlighted
then click edit
then click format as ext3
then set the mount point as   /
just the slash

Ok, that worked! Now I have this message coming up telling me that it's recommended to use a separate partition as a swap drive. I want to use my largest partition as a swap drive. How do I do this? 

[IMG]http://i78.photobucket.com/albums/j81/pat666rick/Screenshot-2.png[/IMG]

---

### Post by Vorteilspreis on 2008-04-04
BTW, should I make the partition that ubuntu is gonna be installed on my primary or logical?

---

### Post by misfitpierce on 2008-04-04
Primary and you can make the swap logical... Thats how I set it up on desktop and it worked out fine.

---

### Post by paydaydaddy on 2008-04-04
swap is a small partition which is generally double the size of your installed RAM system memory. My swap partition is 2gb.

---

### Post by Vorteilspreis on 2008-04-04
I won't lose any date if I click on edit on my biggest partition and make it swap right?

---

### Post by joshrobinson on 2008-04-04
you dont need a really large swap file, a general rule of thumb is 2x what your ram is, if you have 1gig of ram, make it 2gig, if you have 512mb of ram, make it 1gig

so if you have to, you can resize your old windows partition, and make a swap out of it and your root / partition

---

### Post by joshrobinson on 2008-04-04
> **pat666rick said:**
> I won't lose any date if I click on edit on my biggest partition and make it swap right?

to make it swap, you would have to format it, so yes

click your old windows partition, and go to DELETE, make sure you delete the right one
then click NEW, and make 2 new partitions one a small swap partition, and a large one your / partition

---

### Post by StooJ on 2008-04-04
Are you sure Windows isn't installed on sda1? That's what I would usually expect to see...

Your swop partition should be about double the size of the ram in your computer: if you have 1GB of RAM, then make your swop partition 2GB

---

### Post by tangibleorange on 2008-04-04
The swap partition is a partition in its own right of type "linux-swap", so you can't store any other data on it. Resize your largest partition, taking off about 2x your RAM (so 1GB RAM = 2GB swap) and format that as type "linux-swap" (doesn't need a mount point)

---

