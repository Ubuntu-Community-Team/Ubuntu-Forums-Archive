---
title: "New to this..."
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by jkblacker on 2007-04-27
Hi everyone,
Have only just registered though I've been observing for a little while! Got round to burning the iso of feisty fawn earlier today, and I just want to ask a few things before going fully ahead with installation (typing this from the live cd, of course!):

I have an old dell inspiron 6000 (1.83GHz, 512MB RAM, ATI Radeon something) and from everything I've read I should be ok to run ubuntu (plus, the live cd looks like it's doing fine!). However, I don't want to install it on my 80GB laptop HDD, but instead put it on my nice brand spankin' new 250GB WD MyBook, while leaving space on the MyBook for back-ups of my laptop (as well as creating a dvd archive of the laptop soon, just in case...). I know this probably isn't entirely sensible, but hey, once I've got more experience of ubuntu I'm going to be building a new box for it entirely (dual boot with xp then as well, just for when I want it, but that's not the question in hand).

Basically, (I've rambled enough...sorry!) how do I get two partitions (and a third 'swap' partition, if I've read everything right - see, I've been trying to learn!) from the one partition (fat32 as it came) of the mybook? I did start the installation but couldn't work it out, and most documentation I've seen around refers to the 6.10 installer, which seems to be a lot different from 7.04...

Many thanks for helping a young beginner!

Josh

---

### Post by bobplano on 2007-04-27
you resize the existing partition(fat32). make sure it is defragged so you don't lose anything. there should be automatic options that let you resize it and just put in what percentage of the drive you want ubuntu to have. yes you are correct about the partitions, many people have 3, but you can just have root and swap if you want.  if you want to do manual just resize then make 2 ext3's, one for home the other for root and a swap partiton then choose the right mounting and then it shoudl install

---

### Post by mikesignguy on 2007-04-27
gparted is the program you want to use to move the fat32 around so you have space to install Ubuntu...look in the listed programs on the live cd...you may need to type gparted in a terminal. ( not sure)

i usually use a separate cd with gparted on it ...why ??/ it is sometimes quicker

---

### Post by theredcross on 2007-04-27
the latest (2? 3?) ubuntu livecd installations come with a very nice partition helper, and the default option should be to resize a current partition, which a nice slider for easy graphical representation. Just make sure you are resizing the hard drive you want to use.

---

### Post by psionyk on 2007-04-27
to add a couple of things to bobplano's advice too:

1. It's a VERY good idea to not only defrag your windows partition before resizing it, but if you haven't already done so, make backups of your important data as well.  I've resized my windows partition several times now and never had a problem, but better to be safe than sorry.

2. For the swap partition, although there are debates whether it's necessary or not, it's usually a safe bet to make it double your RAM size, that way you have room to spare for hibernation purposes, or if for some reason a running program starts swapping out a lot of memory to the hard disk.  If you choose to go with a seperate home partition, that should be your biggest one, since that is where you would be keeping all of your data and personal files.  The benefit of using a seperate home partition is that if you need to reinstall Ubuntu at any point in the future, that partition can be left on the hard drive so you won't lose your files.

Good luck, and don't be afraid to ask us if you need more assistance! :)

---

### Post by jkblacker on 2007-04-27
Wow thanks for all the speedy replies and advice!

I'm into the idea of having a home partition...So my swap one should be about a gig (double my RAM), but how big should the home and root partitions be, relatively? Obviously the home one will be a lot bigger, but how large does the root need to be?

Thanks again,
Josh

---

### Post by bobplano on 2007-04-27
root should be about 10gigs or more because the programs you install go there. you don't want a too small one because then it will fill up quickly. the home partition can be as big as you want because it holds all your personal files. mines ~15gigs but it can be bigger

---

### Post by jkblacker on 2007-04-27
Brilliant, thanks - will now get this thing installed. 
I'm guessing that it installs in the partition I select as /, and the home one should be labelled /home? I'll be back if that doesn't work! (I harbour secret fears it will install on my laptop hdd and wipe it...)

---

### Post by jkblacker on 2007-04-27
Ok...this is the error message I got:
> The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/My\040Book

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

There are no other applications open and this is the first partition (that I intend to use for access from windoze) on the hddd. Any ideas? The two options are 'go back' and 'continue' but neither leads me anywhere, just round in a circle. It's 1.15am here now so I'm going to go to bed and try again in the morning, hopefully with some great advice from you all if anyone has any ideas?

Thanks again, Josh

---

