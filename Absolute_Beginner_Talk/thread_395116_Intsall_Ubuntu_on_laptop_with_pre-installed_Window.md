---
title: "Intsall Ubuntu on laptop with pre-installed Windows.  Possible?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-03-27
SOLVED

i have a dell xps m140 laptop that came pre-installed with windows xp media center edition.  i would like to be able to install ubuntu eventually and make it a dual-boot system.  the only problem is that since windows was pre-installed, i got no options on how to partition the hard-drive and am now left with a completely windows drive.  can i still install ubuntu overtop it?  and if so, how can i do it without losing windows data?

---

### Post by max.diems on 2007-03-27
You can /probably/ uses GParted to change the size of the Windows partition, but back up everything first Just In Case.

---

### Post by techstop on 2007-03-27
I am quite sure that when you boot with the LiveCD and start the ubuntu installation, it will detect the existing windows installation and ask what you want to do. Your options will be something like

a) erase entire disk and let ubuntu partition drive
b) reduce the size of the windows partition and use the free space to install ubuntu
c) manually partition disk

Of course, you want b). Note that to dual boot, you always have to install windows first, and then linux, because linux is windows aware, but the converse is not true.

If it all falls in a heap I'm sure Dell provide the option to restore your windows installation anyway. Backup your important data before you do anything though.

---

### Post by locke.dragon on 2007-03-27
what's the risk of doing this?  i'll back up my data if i do, but what could happen if something went wrong?  and actually i'm frantically trying to find a way to re-install windows at the moment.  :P  viruses, spyware, adware, trojans, the works.  WHAT FUN!!!  -TOTAL sarcasm-

---

### Post by Sqwishy on 2007-03-27
Yes it's very easy, when you download the ubuntu iso file and burn the cd you boot from at and click on the install icon. After a few steps it will ask you what to do with your hd, it will display options like reformat drive, automaticly use unpartition place, manualy edit, you should probobly be able to choose the top (i think) option that lets you reduce the size of windows by a certain percentage. That  should do everything automaticly for you. When you boot next time the bootloader that Ubutnu installs will give you the choice of choosing windows or ubuntu

---

### Post by theonlyrealperson on 2007-03-27
I used Gparted on a Knoppix Live CD to partition my drive.

First, you want to turn off your swap file in Windows, so when you defragment you can push everything to one side of the disk (the swap is protected, so it shows up as a "immovable" file).

Run defragmenter a couple of times.

reboot into Knoppix live CD (or the Ubuntu live CD, I just used Knoppix)

Then you can repartition the drive without disturbing Windows.

After you create a >10Gig partition, you can install Ubuntu on that partition. 


That's what I did on my IBM Laptop, and it works great. It's easiest to let Ubuntu install the Grub boot loader, rather than trying to set up the Windows one.

****Remember to back up all your important Win files just in case****

---

### Post by Sqwishy on 2007-03-27
> **locke.dragon said:**
> what's the risk of doing this? Not much in my experience, the program that ubuntu uses for partitioning (called gparted) is pretty safe and i've resized my partitions several times and i've never lost any data.

---

### Post by K7KEV on 2007-03-27
No Problem.  Brung your XP to a halt, turn computer off.  Put the Ubuntu distribution disk in.  Run the install program with Ubuntu.  Give Ubuntu people some credit.  It works like a charm.  Something I can't say for the XP.  After Ubuntu install, when you reboot you will get a "GRIB" screen that allows you to select which operating system you want to use.  From there, it's just like booting XP (or Ubuntu).  

PS: I'm a rank newbie too.  I fretted for weeks before I jumped in.  Actually Microsoft finally pushed me in. . . .

Keith

---

### Post by theonlyrealperson on 2007-03-27
> **Sqwishy said:**
> Not much in my experience, the program that ubuntu uses for partitioning (called gparted) is pretty safe and i've resized my partitions several times and i've never lost any data.

Really? Several times? I've wanted to make my Ubuntu partition a little bigger, but was nervous to mess with it a second time.

---

### Post by nike984 on 2007-03-27
As other ones pointed out, use Gparted live CD to reduce the size of 
window partition, and make a new linux partition to the space that was
created after reducing the window partition.

Then installing linux will be straight forward.

---

### Post by az on 2007-03-27
> **theonlyrealperson said:**
> I used Gparted on a Knoppix Live CD to partition my drive.


The Ubuntu installer uses the same programs that Gparted and Knoppix use.  The Ubuntu installer is easier to use - all you have to do is pick the option you want and it will automagically (and safely) create the partitions you need.  You can do it by hand if you want to, but I recommend letting the installer do it.

---

### Post by medley on 2007-03-27
> **locke.dragon said:**
> i have a dell xps m140 laptop that came pre-installed with windows xp media center edition.  i would like to be able to install ubuntu eventually and make it a dual-boot system.  the only problem is that since windows was pre-installed, i got no options on how to partition the hard-drive and am now left with a completely windows drive.  can i still install ubuntu overtop it?  and if so, how can i do it without losing windows data?

You'll have no problem doing this...my laptop is a Dell XPS M1210 and I have it configured to dual boot XP/Kubuntu. You'll see a graphical display of the free space on your drive. If your system is still fairly new, you can probably divide your drive into two partitions. The install utility will detect that another OS is present and offer to set up a dual boot system for you. 

Once you've used Ubuntu for a while, you may find you never use the XP boot. That's the case on my portable. I a number of other Windows system if I need them; but if there is no specific reason that I need Windows, I find myself going to one of my Kubuntu systems.

---

