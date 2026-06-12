---
title: "floola, mount on boot, partition questions. Thanks"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by BrandnewJesus on 2007-10-30
First off I just have to say, this is only 4th day running ubuntu and I LOVE IT!
Its freedom, and its fun, I really enjoy learning this stuff. Everyone is such a great help.
Just a couple questions though...

1. I was trying to install floola, but could no figure out how to do so. I did find an alternative, amarok which was already in the add remove, but wanted to know for future reference, how to install an app I found online. I installed the package libnotify-bin and confirmed it was installed in synaptic, downloaded floola to the desktop(&extracted it), but when i clicked nothing happened. It was not added to the add remove. any link to a forum page already discussing this issue, or an answer would be appreciated.

2. second, I am duel booting windows, (school requires lots of that garbage), and I have around 2000 songs in the itunes folder. I mapped amarok to that folder so i can open my music files, but it seems that the drive has to be mounted in order for it to see it. I know it only takes 2 seconds to mount the drive, but is there any way to have it mount when I boot?

3. When I installed ubuntu, I first did a clean install of windows, partitioned the 70g drive into 2 partitions. one 30g for windows, 1 30g for ubuntu, and left some free. When i went through the ubuntu install i was pretty certain I had it set to install on the second 30g partition, but it seems that it decided to go to the free space instead, leaving me with little room for ubuntu. (I first tried the manual way, but couldent get the right combination of root, swat, ext2, 3 so i gave up)  Everything works fine, I am just a little nervous about going into gparted and trying to extend the 10g partition. is this my best option? or is there someway to just format the 30g partition and use it to store the big music and video files, and just map to it when needed? right now that partition is showing as lost+found. (What is that?)

sorry its so long, thanks in advance.:guitar:

---

### Post by justsomedude on 2007-10-30
> **BrandnewJesus said:**
> 1. I was trying to install floola, but could no figure out how to do so. I did find an alternative, amarok which was already in the add remove, but wanted to know for future reference, how to install an app I found online. I installed the package libnotify-bin and confirmed it was installed in synaptic, downloaded floola to the desktop(&extracted it), but when i clicked nothing happened. It was not added to the add remove. any link to a forum page already discussing this issue, or an answer would be appreciated.

Floola currently doesn't work in Gutsy. As it is not open source, we have to wait for the guy who programs it to fix it. Floola doesn't need to be installed, you just click on the app (theoretically).

The best way to install applications is through Synaptic. You can also use command line *sudo apt-get install [name of app]*, which is the same thing as using Synaptic. Synaptic is just a GUI for apt-get. Deb files can be installed by clicking on them. If you cannot find an app in Synaptic or cannot find a deb file, chances are you can find a tarball (tar.gz). These have to be unpacked and compiled. Sounds very complicated, but it's usually not. I'm sure you can find more information on how to compile stuff in the wiki. There are plenty more options how to install software, you'll get to know them with time.

> 2. second, I am duel booting windows, (school requires lots of that garbage), and I have around 2000 songs in the itunes folder. I mapped amarok to that folder so i can open my music files, but it seems that the drive has to be mounted in order for it to see it. I know it only takes 2 seconds to mount the drive, but is there any way to have it mount when I boot?

You can automount partitions by editing your fstab file. You'll find information here:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Do NOT (!!!) mess with this file unless you know what you're doing.

> 3. When I installed ubuntu, I first did a clean install of windows, partitioned the 70g drive into 2 partitions. one 30g for windows, 1 30g for ubuntu, and left some free. When i went through the ubuntu install i was pretty certain I had it set to install on the second 30g partition, but it seems that it decided to go to the free space instead, leaving me with little room for ubuntu. (I first tried the manual way, but couldent get the right combination of root, swat, ext2, 3 so i gave up)  Everything works fine, I am just a little nervous about going into gparted and trying to extend the 10g partition. is this my best option? or is there someway to just format the 30g partition and use it to store the big music and video files, and just map to it when needed? right now that partition is showing as lost+found. (What is that?)

sorry its so long, thanks in advance.:guitar:

What is best for you depends on your current partition table (which I don't know) and your needs. I suspect Ubuntu installed with the option "use biggest free space" (or whatever it is called), so you will have a root partition and a swap partition. 10 GB for root and swap is ok, you could for example format the 30g left with ext3 and store your data there. Having your data on a separate partition from root is generally a good idea. This way, it will be safe in case your root partition gets corrupted somehow. 

Explaining all your options about partitioning is too much to write here, do some reading and you will come up with a solution which best suits your needs. Formatting the 30g with GParted isn't difficult and won't take long (just make sure you choose the right partition to format).

---

### Post by BrandnewJesus on 2007-10-30
Hey thanks alot for taking the time to answer my questions, you were a great help. I think I will heed your warning, and just take the 2 seconds to mount the drive. I also took your partitioning advise, and everything is working great. Thanks again.:)

---

### Post by BrandnewJesus on 2007-10-30
Just to let everyone know, I ended up going into gparted, created a bigger swap (212 to 1.5 g), and set the 30g+ free partition not being used as fat32. I can now save files to that partition in Ubuntu and windows. :)

---

