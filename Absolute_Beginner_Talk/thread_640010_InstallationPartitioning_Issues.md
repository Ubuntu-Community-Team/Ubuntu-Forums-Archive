---
title: "Installation/Partitioning Issues"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by woodslanding on 2007-12-13
Hi all!

I have just installed Ubuntu Studio 7.10 on my #2 laptop, replacing a second boot of XP, but am considering reinstalling with more partitioning.  It's taken over a dozen installs to get this far, so one more hardly seems like a big deal.  It goes pretty quickly now....


I found a recommendation here in the stickies about partitioning, but it included none of the following info:

What is the significance of /home, /root and /whateverelse? 

How much space does the install require for each of the /partitions?

What are they used for?  Where does user data go?  where does program data go?  How big does the swap partition need to be?  Is swap size a function of my user RAM?  How does its size affect performance? 

I have about X gb to devote to Ubuntu, for the moment.  How should I best partition that?  (In my case it's about 10 gig)

Partitioning seems like the VERY FIRST issue that should be addressed in a beginner forum, as you have to make this decision on install!!

My installation problems so far:

1. PARTITIONING  
The partitioning is very confusing.  I wish it could read my windows partition names, so I could have some confidence I'm not wiping valuable data.  At least, you should have a help screen there that explains the linux partition naming convention!  

The 'resize partition and install' option is confusing, because it looked to me like you were choosing how much space to use for ubuntu, when in fact you are choosing how much space to LEAVE FREE on the partition.  Since I wanted to use the whole partition for ubuntu, I chose 'maximum' and got the tiniest possible install!  oops!  I think this needs to be made clearer.

The installer does not automatically create any additional partitions past /root and /swap.  It would be good to have a semi-manual install option, where there is some explanation of what additional partitions you might want and how big you might want them to be.

2. PACKAGE OPTIONS
The other install problem is that all the packages, upto and including the desktop gui are disabled by default, and the enter key on that page is used to leave the page, not select the package!

So my first install had no desktop.

3. GRUB
Also, some background on the significance of the various options for how and where grub is installed would be very useful.

Anyway, thought I'd mention this stuff, because I think you lose 80% of your users in the first few hours.  Your installer is your ambassador!!

cheers!
-eric

---

### Post by purdticker on 2007-12-13
I'd agree, the installer is tough for users who are trying to dual boot.  There's no "Dual boot" option.  But then again, neither does windows ;)

1. Partitioning
When you installed windows, did you install to a partition taking up the entire disk space?

2. Packaging options
What do you mean all packages are disabled by default?  When you insert Ubuntu install cd, does it load the ubuntu desktop?  Or can you only see command line stuff?

3. Grub
I've also found this to be very confusing.  I just know that if you install windows first, then ubuntu, your grub will automatically show both windows and ubuntu on start, defaulting to ubuntu if you don't select anything.  If you install windows second, it replaces grub with its own, and you cannot get to ubuntu anymore (for us newbs).

For a newbie, I wouldn't worry about grub yet, just install windows first and then ubuntu second, the installer will take care of it for you.

---

### Post by Dr Small on 2007-12-13
For installing a dualboot system, please read this:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Dr Small

---

### Post by dstew on 2007-12-13
> What is the significance of /home, /root and /whateverelse?
These are **mount points**, which are the names of the directories in your Ubuntu file system where the partitions will be attached. You only need two partitions, a root and a swap partition. The mount point of the root partition will be / and the swap partition doesn't really have a mount point, since it will not be part of the file system (the installer might want you to give it a 'swap' mount point just to be sure that it is a swap partition, I don't remember). A separate partition can be created and attached to the /home mount point if you want. Otherwise, the /home directory will be a subdirectory of the partition that is mounted at '/' (the root partition).

> How big does the swap partition need to be?
It should be on the order of your RAM size, maybe twice as big.

> The partitioning is very confusing. I wish it could read my windows partition names, 
The Linux partition names take some getting used to, but they are really more accurate than WIndows names. For example, is C: the name of a disk or a partition? In Linux, the nomenclature is much less ambiguous. /dev/hda1 means "the first partition on hard disk A". You will be able to tell which Linux names correspond to which Windows names by looking at the properties of the partitions using a command such as** fdisk**.

---

### Post by chadridesabike on 2007-12-13
I disagree with a dual boot being difficult.  My first attempt at linux was with dapper drake and i dual booted it no problem.  Fortunately, ubuntu has a great install disk as far as a dual boot is concerned.

first suggestion: get rid of xp.  It is worthless and no where near as fast as any linux distro

Second: since you already have ubuntu installed, use a program like partition logic.  It is free and runs as a live disc would.  Use this to resize your partitions.

Third: make sure you back up your data before you do it.

Cheers!

---

### Post by Presto123 on 2007-12-13
> **chadridesabike said:**
> I disagree with a dual boot being difficult.  My first attempt at linux was with dapper drake and i dual booted it no problem.  Fortunately, ubuntu has a great install disk as far as a dual boot is concerned.

first suggestion: get rid of xp.  It is worthless and no where near as fast as any linux distro

Second: since you already have ubuntu installed, use a program like partition logic.  It is free and runs as a live disc would.  Use this to resize your partitions.

Third: make sure you back up your data before you do it.

Cheers!

The Gparted CD is also nice. :)

---

### Post by kefurd06 on 2007-12-13
> What is the significance of /home, /root and /whateverelse?
What are they used for? Where does user data go? where does program data go? 
/ is like c:\
/home is where profiles are stored (like \Documents and Settings in XP or \Users in Vista)
/root ...i dunno.
i recently figured out that /usr/share is like \program files

> How big does the swap partition need to be? Is swap size a function of my user RAM? How does its size affect performance?
i have read in several places that you want your swap to be between 1.5x and 2x your physical RAM. i have two gigs of ram on my hp notebook. i have yet to fill it. i think one time i set a record of using just over a gig of memory, and i had about two dozen programs open (various audio, video, internets, photo-editing, etc). i'd just set the swap up for 1 gig and be done with it.

---

### Post by g2g591 on 2007-12-13
/root is roots home folder (<1Mb needed here, mines only 39Kb) I recommend 3 partations, the / partation (required anyway) a /home partation, (so if you must reinstall your personall files are safe) and a swap partation (around 1-1.5 Gig should be fine)

---

### Post by woodslanding on 2007-12-13
Thanks All!!  That was quick!

About all packages:  

there is a screen in the gui-based installer for Ubuntu Studio that asks which packages you want to install. ('Packages' might not be the correct terminology here?!)  The first is the gnome desktop, the rest are packages of Music and Video programs.  They are all deselected by default.  Press enter, and you've got an installation without a gui!

Wiping windows:  

Someday, I hope.  But I have yet to get my wireless card working under windows, so I'm not wiping it yet!!  Eventually, I hope to run whatever windows programs I still need under wine....

Ubuntu install link:

The ubuntu studio disk does not seem to have the live disk option--it goes straight to the installer.....

Confusing partitioning:

Thanks--I'm getting clearer on the linux nomenclature, but I still think an explanation on the partitioning page would be helpful!

---

### Post by woodslanding on 2007-12-13
> **g2g591 said:**
> /root is roots home folder (<1Mb needed here, mines only 39Kb) I recommend 3 partations, the / partation (required anyway) a /home partation, (so if you must reinstall your personall files are safe) and a swap partation (around 1-1.5 Gig should be fine)

Ahhhh, thank you!!  This is exactly what I wanted to know.  But any sense of what % of space to devote to /home???  I don't yet understand where files will end up.  Which folder will program files go in?  Documents?

I will be freeing up the rest of the drive over time for data, so It's mostly important not to run out of space in which to install programs.....

Thanks again!
-eric

---

### Post by kefurd06 on 2007-12-13
> **woodslanding said:**
> Ahhhh, thank you!!  This is exactly what I wanted to know.  But any sense of what % of space to devote to /home???  I don't yet understand where files will end up.  Which folder will program files go in?  Documents?

I will be freeing up the rest of the drive over time for data, so It's mostly important not to run out of space in which to install programs.....

Thanks again!
-eric

i believe most software installs to /usr/share (so all users can run the stuff). so far all i've installed that didn't install there was google earth (isntalled to my user folder

so, in short: software installs to /usr/share , and your files are stored in /home/woodslanding

percentages? that's a tough one. depends on how much software, and the size of the software, u install. also depends on how much your personal pics, docs, vids, and other various projects will take up.

---

### Post by woodslanding on 2007-12-14
Okay, cool, that's what I wanted to know.  Well, here I go, wish me luck

---

### Post by kefurd06 on 2007-12-16
lemme clarify a bit there.. /usr/share is where data files n such is stored, similar to program files, except that most of the actual programs are stored in /usr/bin . so if for instance u want to open a file with a certain app, like deluge bittorrent client, u would browse to /usr/bin and find deluge. but if u want to assign a launcher the deluge icon, u would browse to /usr/share/deluge (and then to /pixmaps where the png icons for deluge are stored)

---

