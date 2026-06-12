---
title: "i did something very wrong..."
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by agengo02 on 2008-03-22
so i was messin with Linux mint last night and decided what the heck ill dual boot on my main pc (the one im currently on.) i dont think i did the partitioning right because i kept getting an error with something about ext3 failed. i thought no biggie, i shut down and went on about my night. started up today and boom system fatal error! did i seriously just wipe out my hard drive?!?!?!?!? is there any way i can at least get my files back??? HHHEEELLLPPP!!!

---

### Post by kazamx on 2008-03-22
When you boot up what exactly do you see.

can you describe to us in a little more detail exactly what options you picked when you tried to set up your new partitions.

The more info you can give us the easier it will be to help you

---

### Post by agengo02 on 2008-03-22
ok i didnt do any partitioning before running the boot disk and decided to let linux do that for me.  when installing it would start and about 3 minutes later an error would come up saying that ext3 failed.  i used the guided partitioning (not manual) and let it go from there.

ok it says step 4 of 7.

only options i have is guided - use entire disk (ide1 master (had) - 160.0 GB wdc wd1600bb-22wao)

clicked forward on that.

---

### Post by kazamx on 2008-03-22
I am not 100% sure on this, but I believe that the guided option uses the whole harddrive and replaces any current OS on there. I have never used guided as I always use manual so I hope that I am wrong. 

If you have replaced your windows partition then it could be that your data is lost, please please tell me you have backups. This is out of my experience range and I am not in a position to offer good advice here. Don't panic, check google and keep checking here for updates.

---

### Post by agengo02 on 2008-03-22
oh of course i DONT have anything backed up.  do you think if i go back and do a manual partition it will at least let me access the stuff?  i think ill try that.  thanks man.

---

### Post by kazamx on 2008-03-22
Wait

Don't change anything further. Please just hold on and do a little more research before you change anything. I know there is software out there that can recover data from borked harddrives, maybe someone here knows better than I do. Please don't change anything until you know where you stand.

Information is king.

---

### Post by linuxtoindia on 2008-03-22
just wipe the error partition and then reinstall!
or get the edubuntu cd and perform the repair opearation from there

---

### Post by forestpixie on 2008-03-22
In fact I would shutdown and boot the livecd - then at least there is no more access to the drive until you know what you can do or not as the case may be

---

### Post by forestpixie on 2008-03-22
> just wipe the error partition and then reinstall!

that's not a good idea when the op is trying to salvage a previous mistake

---

### Post by linuxtoindia on 2008-03-22
or try running live cd get the datas back and then wipe out everythg! then come back to linux.. and its advisable to keep also windows on ur disk

---

### Post by agengo02 on 2008-03-22
im on the live cd right now.  ok after more thinking about what i have i dont feel as bad.  just a bunch of music (replaceable), pictures (which i just recently put all on my mom's laptop when she was in town last week so i can get them again), and a butt load of other useless apps/junk.  so i think im going to continue with the install and partition the whole drive.  thanks guys.

---

### Post by kazamx on 2008-03-22
If your going to do that can I make a small suggestion. partition the drive with say 20gb for a windows install and then a partition for Linux and then another one for "Stuff"

Install windows first, then linux (windows can bork up grub if you install it second). By keeping your important data on a separate partition to your OS's it will be much safer. 

trust me while I love Linux, if your new to it, your going to be much happier having Windows to boot back into from time to time.

---

### Post by ugm6hr on 2008-03-22
> **agengo02 said:**
> only options i have is guided - use entire disk (ide1 master (had) - 160.0 GB wdc wd1600bb-22wao)

I haven't used Mint, but that is odd.

You should have *Guided - use largest free space* and *Manual* options.

Are you sure your CD is genuine?

PS: *use entire disk* means exactly that.

---

### Post by snkiz on 2008-03-22
make a home partition to save some headache when you upgrade

---

### Post by agengo02 on 2008-03-22
done.  im now solely a linux user.  partitioned a 20gig section for when upgrades are available.  thanks for the help guys.

---

### Post by tvtech on 2008-03-22
do yourself a huge favor and don't let ubuntu do the partitioning for you, although it has a lot of fun features even in manual use a live cd like g-parted[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")
or and this sounds like a must burn yourself a knoppix dvd or if you must the cd it comes with a host of live dvd/cd apps that can really save your *** if you do something stupid like say obliterate your MBR corrupt windows or linux beyond any hope of repair or feel like hacking some ones wep

---

