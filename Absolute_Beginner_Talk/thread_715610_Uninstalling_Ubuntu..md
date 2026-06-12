---
title: "Uninstalling Ubuntu."
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by fly* on 2008-03-05
Hi All,

Now before I get a flurry of posts saying how can I consider uninstalling Ubuntu, I would like to explain.

Being an absolute linux newbie I decided to install Ubuntu as a dual boot. I initially thought I was installing Ubuntu Studio but alas it was just the generic version, which altho great...its not Ubuntu Studio. So I then went and installed Ubuntu Studio an d when I was asked what software I wanted to install I pressed the enter key thinking it would mark on the list what I wanted only to find that it just continued with the install and only loaded the shell.. So, not to be detered I tried installing Ubuntu studio again, this time it work like a dream... 

Where my problem comes in, is that all these installs were intsalled as dual boots...so I now have 3 versions of Ubuntu on my system and Windows...all these partitions obviously take up space and I dont really want 3 versions of Ubuntu  on my system..

Now how do I uninstall all 3 versions and just load up the one ???

---

### Post by Oldsoldier2003 on 2008-03-05
> **fly* said:**
> Hi All,

Now before I get a flurry of posts saying how can I consider uninstalling Ubuntu, I would like to expalin.

Being an absolute linux newbie I decided to install Ubuntu. I initially thought I was installing Ubuntu Studio but alas it was just the generic version, which altho great...its not Ubuntu Studio. So I then went and installed Ubuntu Studio an d when I was asked what software I wante dto install I pressed the enter key thinking it would mark on the list what I wanted only to find that it just continued with the install and only loaded the shell.. So, not to be detered I tried installing Ubuntu studio again, this time it work like a dream... 

Where my problem comes in is that all these insttalls were intsalled as dual boot...so I now have 3 versions of Ubuntu on my system and Windows...all these partitions obviously take up space and I dont really want 3 versions of Ubuntu  on my system..

Now how do I uninstall all 3 versions and just load up the one ???
you could boot from the live cd and just delete all of the Ubuntu partions turning them into free space, then install in the free space. look at the bright side, you've got installation down to an art now :)

---

### Post by Gepetto on 2008-03-05
To do it simply, I would just reformat your entire disk, or at least the partitions with Ubuntu on them, and reinstall the one that you want to keep. 

Somebody correct me if i'm wrong here, but I also think you can go into Gparted (whether the one included in ubuntu, or the separate program itself) and delete the other partitions with the other installs, and then recombine those partitons again.

---

### Post by Oldsoldier2003 on 2008-03-05
> **Gepetto said:**
> To do it simply, I would just reformat your entire disk, or at least the partitions with Ubuntu on them, and reinstall the one that you want to keep. 

Somebody correct me if i'm wrong here, but I also think you can go into Gparted (whether the one included in ubuntu, or the separate program itself) and delete the other partitions with the other installs, and then recombine those partitons again.
yes you can do that with a live cd. you cant mess with the active Ubuntu partitions if you actually boot into Ubuntu.

---

### Post by fly* on 2008-03-05
Jees, talk about swift replies... :)

Um, I dont think Ubuntu Studio comes out as a Live CD (when you say Live i'm guessing that means you can boot directly from the disk, if so then no...the iso I have has to install)
> 
To do it simply, I would just reformat your entire disk, or at least the partitions with Ubuntu on them, and reinstall the one that you want to keep.

How would I do this...

Sorry i'm an absolute newbie here....I need things in point form :)  or even a link that lists what I need to do...I have a fair knowledge of windows and OSX but thats where it stops...

---

### Post by prshah on 2008-03-05
Use ANY live (K,X)Ubuntu CD, open a terminal and give the command:

sudo fdisk /dev/xxx

where xxx is your harddisk (1st HDD is sda or hda, 2nd sdb or hdb).

In fdisk, use the "p" command to list your partitions.

Delete all partitions with type Linux, or Linux swap. (use the "d" command and the partition number from the list above.)

At this point, assuming only 1 partition remains (Windows?).

Now, if you are sure, you can commit your changes with "w". then "q"uit.

Restart your computer (sudo restart) and install as you like.

Note: It's better if you have one partition setup with mount point "/" and a seperate partition with mount point "/home", and a third partition (small, maybe 1Gb or less) as swap.

If you are still confused, posting the "p" listing of fdisk will allow others to give you more exact advice.

---

### Post by fly* on 2008-03-05
Thanks prshah :)

I'll give it a bash when I get home tonight....

So far Ubuntu has by far exceeded my original expectations....once this is done i'll be happy sailing.... :)

---

### Post by fly* on 2008-03-06
Thanks guys...all working now :)

---

