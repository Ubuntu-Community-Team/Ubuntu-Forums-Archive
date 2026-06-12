---
title: "What is wrong!?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Booj2600 on 2007-07-25
Alright guys.  I've decided to take the leap and set up a dual boot system with XP and Ubuntu version 7.04.  I've heard all about how easy Ubuntu is to install..  So I can only imagine how dumb I have to be to ball it up.  But here goes. 

I get to step four of the installation, and it shows me two hard drives, one 61.5gb (Master), one 82.3gb (slave).  Before I started this installation, I formatted the slave drive, there should be no more data on it.  So I click Guided - Use entire disk, and then the slave drive (as that is where I would prefer to install it, without taking up the entire drive.  But I don't know how to do that.  That is an issue as well.)  Anyway, after I do that, I go through the rest of the installation, and hit Install at the end.  It starts - then I get this message:

**Failed to unmount partitions**
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/new\040Volume

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

(Go back)(Continue)

Continue takes me back to Step 4 and the drive selection screen.  So what am I doing wrong!?  

Haha..  This is kind of embarrassing.  But thank you guys!

---

### Post by overdrank on 2007-07-25
> **Booj2600 said:**
> Alright guys.  I've decided to take the leap and set up a dual boot system with XP and Ubuntu version 7.04.  I've heard all about how easy Ubuntu is to install..  So I can only imagine how dumb I have to be to ball it up.  But here goes. 

I get to step four of the installation, and it shows me two hard drives, one 61.5gb (Master), one 82.3gb (slave).  Before I started this installation, I formatted the slave drive, there should be no more data on it.  So I click Guided - Use entire disk, and then the slave drive (as that is where I would prefer to install it, without taking up the entire drive.  But I don't know how to do that.  That is an issue as well.)  Anyway, after I do that, I go through the rest of the installation, and hit Install at the end.  It starts - then I get this message:

**Failed to unmount partitions**
The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/media/new\040Volume

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?

(Go back)(Continue)

Continue takes me back to Step 4 and the drive selection screen.  So what am I doing wrong!?  

Haha..  This is kind of embarrassing.  But thank you guys!

Hi and welcome, the drive you are trying to use is mounted by the live cd. So you can right click on the drive and select unmount and then you can continue with your installation. Good luck! :popcorn:

---

### Post by lemonseed on 2007-07-25
> **Booj2600 said:**
>  the slave drive (as that is where I would prefer to install it, without taking up the entire drive.  But I don't know how to do that.  That is an issue as well.)

If you don't want to use the entire drive you can choose Manual. However with doing this you'll have to create the swap partition and the root parition yourself but you will be able to control the exact size of each. It sounds harder than it really is.

This is a basic idea of how to do it manually.

Step1: make the swap partition equal to the amount of RAM you have installed (i.e. 1024MB if you have 1gig of memory). Note: if you have less memory (like 256MB or 512MB) you might want to make the swap partition a little larger like 1.5x or even double (2x). To select it as a swap select "swp".

Step 2: make the root partition to whatever size you desire within the limits of the drive. Say you only want to use 20GB, so enter a number along the lines of 20000MB. Then set it as root with a forward slash "/".

Step 3: Follow the rest of the installation.

Note: granted this is not written out step by step and word for word of the actual install but it should give you an idea.

---

### Post by Booj2600 on 2007-07-25
Okay, great!  That makes me feel silly for having an issue with that..  Well, thank you!  Now, though, I have another issue.  I get a new error message right after step four, saying:

"Parted cannot resize partitions managed by Windows Dynamic Disk."

Okay, even I can understand what this means.  But..  What do I do about it?  I probably seem so helpless.  I'm just not familiar with this aspect of computers!  Sorry!

---

### Post by oilchangeguy on 2007-07-25
simply unplug the drive with windows on it. set the jumper on the drive you want to use for ubuntu to master, and install it. then plug in the windows drive, and set the jumper to slave. and you should be on your way.

---

### Post by Booj2600 on 2007-07-25
Well, if no one says that that is a bad idea, it seems like my only option.  If I do that though, it will still detect my install of XP, correct?  And it won't mess up my system or anything?  And what exactly would I do if I only had one hard drive, which I will on the next computer I might install Ubuntu on.  So what exactly did I do wrong that screwed up my install?  So I don't do it again?

I really have no idea what I did that was so wrong, and I don't see why I should have to open up my machine to fix it..  But if that's what I have to do, that's what I have to do.

---

### Post by Booj2600 on 2007-07-26
Okay.  I did so.  And I apologize for the double post, but thank you all for your advice.  But...

I'm not done yet!  I have Ubuntu installed, everything works wonderfully.  I have Beryl installed too, thinking about getting compiz-fusion..  Will they clash?  That's not my biggest issue though.  I have my other drive (The drive with Windows on it) set to slave and everything, with my Ubuntu drive as the master.  Yet when I boot up, it doesn't detect any other operating systems, just shoots me straight into Ubuntu.  I can read the files on the other driver just fine as well...  Simply can't boot into the OS.  Any suggestions?

Thank you for all your patience, it's really paying off!

---

