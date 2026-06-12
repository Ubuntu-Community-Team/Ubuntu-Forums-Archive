---
title: "Install Second Hard Drive, or Partition Existing Drive to Install Ubuntu?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-03-31
Hello Everyone.  I have finally decided to use Linux after researching Linux and thinking about it for the past year.  I downloaded the latest Ubuntu, and played around with the live CD part, and so far I really like it.  My next step is to install it.

For now, I still need XP.  Should I install a second hard drive, and load Ubuntu on the new hard drive, or should I load it on my existing hard drive?  I am assuming that, if I were to load Ubuntu on my existing hard drive, the install CD will guide me through the loading and partitioning process.

Any help will be appreciated.

---

### Post by brennydoogles on 2007-03-31
> **F_r_e_d said:**
> Hello Everyone.  I have finally decided to use Linux after researching Linux and thinking about it for the past year.  I downloaded the latest Ubuntu, and played around with the live CD part, and so far I really like it.  My next step is to install it.

For now, I still need XP.  Should I install a second hard drive, and load Ubuntu on the new hard drive, or should I load it on my existing hard drive?  I am assuming that, if I were to load Ubuntu on my existing hard drive, the install CD will guide me through the loading and partitioning process.

Any help will be appreciated.

It really depends on what you like!! i recommend installing the second hard drive, and formatting it to ext3 and using it as your home partition. If you do that you will have Ubuntu installed on your windows drive, and all of your personal files will be on a separate hard drive.

---

### Post by F_r_e_d on 2007-03-31
Hey Brenny thanks for the quick response.

Can I assume, then, that one way is not necessarily better than the other way (i.e. second hard drive vs. existing hard drive)?

Also, will I be prompted by the CD on how to do the install, whether I install Ubuntu on the existing hard drive, or get a new hard drive?

---

### Post by ububaba on 2007-03-31
> **brennydoogles said:**
> It really depends on what you like!! i recommend installing the second hard drive, and formatting it to ext3 and using it as your home partition. If you do that you will have Ubuntu installed on your windows drive, and all of your personal files will be on a separate hard drive.

How can one format to ext3? :confused:

---

### Post by Europa2010AD on 2007-03-31
> **F_r_e_d said:**
> Hey Brenny thanks for the quick response.

Can I assume, then, that one way is not necessarily better than the other way (i.e. second hard drive vs. existing hard drive)?

Also, will I be prompted by the CD on how to do the install, whether I install Ubuntu on the existing hard drive, or get a new hard drive?

I just installed Ubuntu on my 2nd HD two days ago. From my experience, I´d say it is much better for a newbie to install it onto a 2nd HD. This is because in order to boot into your desired OS, all you need to do is to choose (in the BIOS) which HD to boot first.

Installing it this way also makes it easier to troubleshoot if something goes wrong with your GRUB settings (do a search on GRUB if you dunno what I´m talking about). I installed GRUB onto my 2nd HD (where Ubuntu sits). I ran into a problem with GRUB and couldn´t boot into Ubuntu OR Windows from the menu... so all I had to do is to go into BIOS and boot from my Windows HD.

---

### Post by NicoleM on 2007-03-31
i personally had a spare hard drive hanging around so i installed ubuntu on the slave drive.  for me that was a little extra insurance should things go horribly wrong (though they haven't...yet) but there's really no one way that's "better"

I was also wary about letting gparted resize my xp partition. although I"m sure it's perfectly safe I prefer to have as much control as possible when it comes to my computer, and I've had nightmares with previous windows repartitioning excursions (mainly with partition magic)

I admit that my reasons are probably considered unfounded by some so it' spurely your personal preference and how you like to organize things.  my preference was to keep things separate.

this site: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) has examples of many different partitioning schemes and all are valid.  

you may also want to check the installation section of the same link as it walks you through what to expect in the installation process including the on-screen partitioning prompts that you were asking about.

i belive that site was created by a forum member, and neither that site nor this forum has steered me wrong yet :)

---

### Post by rok3 on 2007-03-31
> **F_r_e_d said:**
> Hello Everyone.  I have finally decided to use Linux after researching Linux and thinking about it for the past year.  I downloaded the latest Ubuntu, and played around with the live CD part, and so far I really like it.  My next step is to install it.

For now, I still need XP.  Should I install a second hard drive, and load Ubuntu on the new hard drive, or should I load it on my existing hard drive?  I am assuming that, if I were to load Ubuntu on my existing hard drive, the install CD will guide me through the loading and partitioning process.

Any help will be appreciated.

You could defrag your drive and then use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") to repartition your drive.  Chkdsk will have a fit but should correct any errors the next time you log on to XP.  Your safest option would be to install to a 2nd HD if you do not already have free space on your HD on which XP is installed.  Install Grub to the master boot sector and you'll get a menu to choose which OS to boot when you boot.

---

### Post by Europa2010AD on 2007-03-31
> **rok3 said:**
> You could defrag your drive and then use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") to repartition your drive.  Chkdsk will have a fit but should correct any errors the next time you log on to XP.  Your safest option would be to install to a 2nd HD if you do not already have free space on your HD on which XP is installed.  Install Grub to the master boot sector and you'll get a menu to choose which OS to boot when you boot.

I would suggest installing Grub to the master boot sector of the 2nd HD (*NOT* to the HD where XP is), just to be safe.

---

### Post by F_r_e_d on 2007-03-31
Hey thanks everyone for your great advice so far.

In the meantime, I have been researching this issue in the Ubuntu forums.  It sounds like it's best to install a second hard drive for Linux.  I guess I can get into a lot of trouble if I try to load Linux on the same drive as XP, especially if things don't go right.

I hope you'll all be here to help when I start asking the really tough questions!!

---

