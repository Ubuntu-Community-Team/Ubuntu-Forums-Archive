---
title: "Replacing Vista"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-09-11
Hi all, 

my dad has the following laptop

HP pavilion entertainment one. 1.8 GHZ processor 2GB ram

He wants to replace Vista with Ubuntu, but cant do it. I have tried dban, tried dual boot, we have even taken the hard drive out and put it in an external case to format it then tried installing ubuntu. 

The problem we get is a tty error. Have tried 6.10 and 7.04 and neither one works from the iso image. 

Has anyone done this before or is able to offer any help? He has even tried putting XP on it and that isnt happening either.

Thanks

Patrick

---

### Post by ijason on 2007-09-11
it sounds like you may need to make a gparted live cd and boot off that. from your post it sounds like you've already ruined the vista install so there's no concern for saving that. i would just put the HD back into the laptop and boot it off a gparted liveboot disk. from what i hear it's one of the better disk formatting and management tools.

/good luck!

---

### Post by chrome saint on 2007-09-11
I would second the idea of making a GPARTED live CD and booting off it and using it to un-partition the HDD prior to trying the ubuntu CD.

Just as an aside have you checked the BIOS to make sure the laptop is set to allow boot-from-cd to be the first option?

---

### Post by zetsumei on 2007-09-11
I've tried putting Ubuntu on my Vista laptop as well.  I think it's something to do with the filesystem of Vista.  Format the ENTIRE drive to NTFS and then install Ubuntu.  Also, make sure you're using the right Ubuntu install.  If it's a 64 bit processor, then use a 64bit install of Ubuntu.  If 32bit, use a 32bit install.

---

### Post by bone2006 on 2007-09-11
There might be a hidden partition for recovery in the laptop and a setup in the bios that looks for this partition.  I would look around in the bios to be sure if it's there it's disabled.  gparted liveCD and delete everything you see and create a new ext3 partition and you shouldn't have any problems then, seems like you want straight ubuntu and not a dual boot.

---

### Post by ozPATT on 2007-09-11
what is gparted and how do i make it?

we have vista recovery discs and that re-installs vista fine, so no issues with that, but yeah he wants it completely off, so happy to format everything and use the gparted thing, but not sure whta that is or how i go about doing it..

it is a 64 bit processor, so that could well be the problem, but i did download a 64 bit ubuntu but that didnt work either...

---

### Post by dptxp on 2007-09-11
GParted is a program that you can download free, make live CD and boot with it to make partitions.

Make at least 3 partitions - one 6-12 GB in ext3 for / (root), one ext3 partition for /home using rest of disk space (minus 1 GB for SWAP), and one SWAP.

I suggest to make one 6-10 GB extra partition, you can use it for data, and for any other OS (linux) you want to try in furture. Very handy.

Some information at my signature, many at psychocats.net

---

### Post by bone2006 on 2007-09-11
go here [http://tinyurl.com/662ud](http://tinyurl.com/662ud) and grab the liveCD of gparted.  Reboot your computer
Gparted is like partition magic, free and I like it better

---

### Post by Gremlinzzz on 2007-09-11
What kind of tty error. do you have more info on the error?

---

### Post by Gremlinzzz on 2007-09-11
> **Gremlinzzz said:**
> What kind of tty error. do you have more info on the error?

left the error link out here it is.
[http://www.unet.univie.ac.at/aix/aixprob/prbslvgd/ttyerrids.htm](http://www.unet.univie.ac.at/aix/aixprob/prbslvgd/ttyerrids.htm)

---

### Post by hyper_ch on 2007-09-11
get first the 32bit version of *buntu... the 64bit has some more challenges ;)

And if you have Vista installed, use the Vista partition tool to actually resize your partitions and get some unpartitioned space.

Once you done that, I mean once you have unpartitioned space, then use the alternate install cd for the actual installation. That one is better to do an install.

---

