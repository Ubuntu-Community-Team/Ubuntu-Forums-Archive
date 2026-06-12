---
title: "Reinstall  Ubuntu"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by MDSanta on 2006-08-20
I've been messing with ubuntu a bit for the last few months and i've finally managed to break it. I was trying to mess with usplash      
and I guess I missed a step cause when I boot it wont go beyond the initial startup.

so before I reinstall I would to see if I can get a few questions answered.

1. is there anyway I can get to my current setup so that I dont have to reinstall? 

2. assuming I reinstall, is there anyway I can make an image of my setup so in case it does happen again I can just reinstall it and avoid having to setup my system again?

3. I have an 80 gig partition that has at least 30 gigs being used. If i attempt to break the 80 gigs into two 40 gig partitions will I lose those 30 gigs of data?

4.how are you today?

2 to go

5. is there any way I can give each workspace its own different wallpaper?
6. a few months ago I saw a screenshot of ubuntu desktop in which the users workpanel thingie showed all 4 windows as really small screenshots in color and stuff. does anyone know how i can set this up? 


thank you }:o)

---

### Post by Qrk on 2006-08-20
1) Have you tried the recovery mode. (I don't think it will work but it is worth a shot.)
2) Yes. When you boot into the Live CD to install Ubuntu, you can use that environment to make a backup of your data. I'd save your home directory (tar it, then save it to a USB stick or burn it to a CD) as well as the contents of /var/cache/apt/archives. Your home directory contains your configuration, and the apt archives contain all the programs you've installed, in .deb format.
3) You shouldn't, but I've found that the installer has a harder time of resizing ext3 partitions than it does ntfs partitions. 

4)Very well

5) Not in gnome, KDE has this feature
6) That is probably part of Xgl/compiz. There are guides on this forum for how to get that set up. (I think you are talking of miniwin)

---

### Post by kebes on 2006-08-20
> **MDSanta said:**
> 1. is there anyway I can get to my current setup so that I dont have to reinstall?

Yes I'm pretty sure you can recover from the current problem. Probably it's just your bootloader that's messed up. You can reinstall grub from scratch and this will probably fix everything. For instance see these instructions:
[http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation](http://ubuntuguide.org/wiki/Dapper#How_to_restore_GRUB_menu_after_Windows_installation)

They apply to fixing grub after a Windows install, but similar advice applies in your situation. Briefly, you can boot into the Ubuntu 6.06 CD, which provides you with a LiveCD environment. From there you can run "grub-install" from the commandline, or you can use "grub" and enter the parameters for you system one at a time. After this, a fresh grub should be installed to your master boot record (MBR), and everything should boot up fine. If you need to fine-tune it (change the default, add a windows partition), you can edit the file "/boot/grub/menu.lst".

If you run into problems, search the forums and/or post more questions. Breaking/fixing grub is something that happens frequently enough, so you should be able to get help on that.

> 2. assuming I reinstall, is there anyway I can make an image of my setup so in case it does happen again I can just reinstall it and avoid having to setup my system again?

Yes. You can use a program called "partimage" to make images of your hard-drive partitions. What I do is have an extra partition on my hard-drive for saving these images. (I also burn them to DVD every so often.) The easiest way to use partimage is to burn a LiveCD that has partimage installed. For instance, the "System Rescue CD" will let you do this:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Basically you boot into this CD, then mount the partition you want to *save images to* (but NOT the partition you want to backup), and run partimage:
```

cd /mnt/
mkdir images
mount /dev/hda6 images
partimage

```
(Obviously change "hda6" to point to the partition where you will save the images.) You then have the option of picking the partition to backup, or restoring an old image. Partimage can also save the image over the network (or even burn a CD image), but this can be more tricky.

Partimage works great and is useful for saving a known "good" configuration.

> 3. I have an 80 gig partition that has at least 30 gigs being used. If i attempt to break the 80 gigs into two 40 gig partitions will I lose those 30 gigs of data?

You can retain the data. You can boot into any LiveCD that has GParted installed. For instance, you can boot into the Ubuntu 6.06 CD, and then run GParted. This will give you the choice of formating, resizing, and moving partitions. The data in the partitions will not be erased. So yes, you can take an 80 gig partition and shrink it to 40 gigs.

As always, use these tools with caution. They normally work, but you should ALWAYS back up your important data before doing this kind of thing!

> 4.how are you today?
I'm pretty good. It's raining today so I'm a bit cold, but other than that things are great.


> 5. is there any way I can give each workspace its own different wallpaper?

I'm a KDE user. In KDE I know you can right-click on the desktop, select "configure desktop" and then on the "desktop" tab you'll see an option that says "for all desktops" which you can change to "desktop 1" and so on. This lets you configure each wallpaper seperately. I'm not sure how to do it in Gnome, but it's probably similar.

> 6. a few months ago I saw a screenshot of ubuntu desktop in which the users workpanel thingie showed all 4 windows as really small screenshots in color and stuff. does anyone know how i can set this up? 

There are now a number of "fullscreen task managers" available for Linux. It was probably "Komposé":
[http://kompose.berlios.de/](http://kompose.berlios.de/)

Which lets you assign a key/screen-corner for fast application switching. It's a neat little app, however it is painfully slow on older hardware. It can take several seconds to draw out all of the mini-windows on a modest computer. It's worth trying out, but be warned that on some systems it doesn't perform nicely.


> thank you }:o)

You're welcome. If you need further clarification on any of my answers, feel free to post again.

---

