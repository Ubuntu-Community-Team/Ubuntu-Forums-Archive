---
title: "Partitioning for Kubuntu"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by carpola on 2007-07-19
Ok, so I've used ubuntu a little and decided that I don't like GNOME so I thought I would install kubuntu for KDE on my new laptop with a single 160 gig harddrive. However, unlike the installation of ubuntu, my two options for partitions to install kubuntu were to wipe my harddrive clean or to do it manually. I've tried all the options and looked through various threads, but for some reason, I can't seem to be able to do it correctly without destroying everything. Can somebody give me steps?

---

### Post by AlexenderReez on 2007-07-19
i suggest to use manually partitioning , then figure out and manage partition with gparted..if you do it carefully ,you won't warm your laptop...but if it is still problem there...i doubt that about bug exist there....many bugs reported for partition process...in testing period ,so if it is version that has been released..it should not contain a bug

---

### Post by BlahMan_of.Doom on 2007-07-19
Do it manually. Okay, let's say your other partition was an NTFS partition. Now, right click on a partition, then hit "New..." then make an ext3 partition, however big you want it, and make it mount on "/" (without the quotes). Then make another drive, at least 2GB, as a swap-linux (I'm pretty sure that's what it's called) partition. Select the "/' partition, and install (K/X)Ubuntu on that.

---

### Post by carpola on 2007-07-19
ok, so i'm using qtparted, since this is kubuntu and not gnome, but how can i be sure i'm resizing my main and ONLY harddrive so that everything that's saved on the 50gigs or so in use will not be destroyed when i take free space from that partition and create a new one for linux?

---

### Post by carpola on 2007-07-19
i don't know if you saw my last post or not because it was posted the same time yours was.

---

### Post by carpola on 2007-07-20
should i just GPARTED from the command line and use that to possibly downsize a partition so that i can install kubuntu? i don't know why the install for kubuntu didn't work like it did for ubuntu!

---

### Post by ubanchaos on 2007-07-20
so do u wanna dual boot if so u need to gparted and make 2 partions and dual boot it so later on 
GRUB will ask you whick OS u want to load

---

### Post by meierfra on 2007-07-20
Why to you want to partition the hard drive?   Just install  the "kdesktop" via 

```
sudo apt-get kdesktop
```

and you will be able to use kde.

Edit:

I just realized that I misread your post.   I thought you are trying to install kubuntu on a machine which currently runs ubuntu. But it seems that you have   new laptop. Is it running Windows XP or Vista?

---

### Post by ubanchaos on 2007-07-20
iiono maybe she want to have windooze on their too

---

### Post by carpola on 2007-07-20
> **meierfra said:**
> Why to you want to partition the hard drive?   Just install  the "kdesktop" via 

```
sudo apt-get kdesktop
```

and you will be able to use kde.

Edit:

I just realized that I misread your post.   I thought you are trying to install kubuntu on a machine which currently runs ubuntu. But it seems that you have   new laptop. Is it running Windows XP or Vista?

It's running Vista. I don't know why the setups for Ubuntu and Kubuntu install cds are different. Perhaps I should just use an Ubuntu cd and just upgrade to KDE desktop? Would it be the same amount of files?

---

### Post by meierfra on 2007-07-20
Did you had vistas on your old laptop. too?  It seems that there are some differences between xp and vistas with respect to dual booting. But I never dual booted with  vistas, so I don't really know.  If you google for "vistas kubuntu dual boot" you will a good number of guides, which you might want to look at.

I did install ubuntu and then added kdeskop.  At  login I can choose between a gnome and kde session. I use kde most of the time, but just once in a while I use gnome, just for the fun of it.  I heard that gnome is more stable then kde, but I never had any crashes (except for firefox  freezing regulary)  

As far as I know, you will have all the kubuntu files plus the gnome files.

---

### Post by AlexenderReez on 2007-07-20
i'm dual booting ubuntu with vista(ultimate) ....

if you want minimal requirement to run kde...you can 

> sudo aptitude install kdesktop

but it is better to install complete set of kubuntu

> sudo aptitude kubuntu-desktop

and if you don't like it...after testing it...you can always just remove it by


> sudo aptitude remove kdesktop

or

> sudo aptitude remove kubuntu-desktop
-->based on your installation:)

---

### Post by meierfra on 2007-07-20
I agree with AlexenderReee.  I meant to say "kubuntu-desktop" every time I said "kdesktop".

---

### Post by carpola on 2007-07-21
Well, what program can I use for free that will allow me to downsize my only partition of Vista so that I can use the remaining disk space for my Kubuntu install?

---

### Post by Beernut on 2007-07-27
I used the disk management tool in Vista.  Here is a link that explains how to do it I feel this is probably the safest way to resize your vista partition.

[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

The link is from the Ubuntu windows dual boot page located here.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Then just install Kubuntu and have fun.

---

