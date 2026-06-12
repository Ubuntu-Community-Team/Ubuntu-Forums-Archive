---
title: "Some Basic Idiot Questions"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Actuary32174 on 2007-12-04
I am interested in putting ubuntu on one of my computers. I am definately not as computer savvy as many of the members of this group. Here is what I would like to know:

1. Currently, XP is running on my computer. If I attempt to install ubuntu on the computer and something goes wrong, how difficult is it to totally remove the program from the computer?

2. Upon bootup, am I given a choice of operating system, XP or ubuntu? 

3. By having ubuntu on my computer, are any XP programs affected or negated?

4. XP is working fine for me. Am I asking for my own trouble by installing ubuntu on my computer? Worst possible senario for me:

     a. After installing ubuntu, I can't even get the computer to boot up.
     b. If it does boot, everything is frozen.
     c. I can't return the computer to its original state.
     d. Some or all of my existing programs are damaged beyond repair or erased. 
     e. After everything comes to a total standstill, I say "God, why did I even start this?"

Any impressions?

Thanks,

Rick

---

### Post by nhandler on 2007-12-04
> **Actuary32174 said:**
> I am interested in putting ubuntu on one of my computers. I am definately not as computer savvy as many of the members of this group. Here is what I would like to know:

1. Currently, XP is running on my computer. If I attempt to install ubuntu on the computer and something goes wrong, how difficult is it to totally remove the program from the computer?

2. Upon bootup, am I given a choice of operating system, XP or ubuntu? 

3. By having ubuntu on my computer, are any XP programs affected or negated?

4. XP is working fine for me. Am I asking for my own trouble by installing ubuntu on my computer? Worst possible senario for me:

     a. After installing ubuntu, I can't even get the computer to boot up.
     b. If it does boot, everything is frozen.
     c. I can't return the computer to its original state.
     d. Some or all of my existing programs are damaged beyond repair or erased. 
     e. After everything comes to a total standstill, I say "God, why did I even start this?"

Any impressions?

Thanks,

Rick

1) You can easily just format the partitions that you install Ubuntu on. That will completely wipe it from your computer.

2) Yes

3) No. Although I have heard about some problems with the clock getting messed up.

4) As long as you install it correctly (there are guides if you need help), you should be fine. However, if you mess up on the partitioning step, you could easily destroy your Windows installation.

---

### Post by mali2297 on 2007-12-04
Try out the LiveCD first. Play around with the applications. If they all work alright (albeit slow) then you can choose to install.

Good luck.

---

### Post by af20001 on 2007-12-04
I would have a read of [this]("http://users.bigpond.net.au/hermanzone/p3.htm") page a few times before you attempt to install for dual boot, to familiarize yourself with any potential pitfalls.

Also, you will want to make sure your hard disk is fully defragged before running the install, to maximize the partition space available to Ubuntu.

---

### Post by SteveHillier on 2007-12-04
> **Actuary32174 said:**
> I am interested in putting ubuntu on one of my computers. I am definately not as computer savvy as many of the members of this group. Here is what I would like to know:

1. Currently, XP is running on my computer. If I attempt to install ubuntu on the computer and something goes wrong, how difficult is it to totally remove the program from the computer?

2. Upon bootup, am I given a choice of operating system, XP or ubuntu? 

3. By having ubuntu on my computer, are any XP programs affected or negated?

4. XP is working fine for me. Am I asking for my own trouble by installing ubuntu on my computer? Worst possible senario for me:

     a. After installing ubuntu, I can't even get the computer to boot up.
     b. If it does boot, everything is frozen.
     c. I can't return the computer to its original state.
     d. Some or all of my existing programs are damaged beyond repair or erased. 
     e. After everything comes to a total standstill, I say "God, why did I even start this?"

Any impressions?

Thanks,

Rick

Take all necessary precautions with your data.  back up anything sensitive.  Although Ubuntu partitioner is good at shrinking Windows partitions and moving data if necessary I would run a windows defrag first just to give myself a comfort level.  
If you have the windows release or recovery disks then returning your system to original state is easy (but remember what happens to device drivers and user files).  If you are really paranoid get your self another hard disk and use that for your Ubuntu partition leaving the Windows disk alone.
Hope some of that helps

---

### Post by hyper_ch on 2007-12-04
worst possible scenario:

Something with the partioning goes wrong and you lose all data that's on it.

--> So you backup your important files first ;)

---

### Post by webdr on 2007-12-04
ALWAYS boot live cd and test functionality FIRST. More important than video is to make dang sure you enjoy inet connectivity when booted to LiveCD, as you will NOT want to fight your way through connectivity issues AFTER the fact.

I've never had a problem yet with Ubuntu installing into resized partitions and automagically configuring dual boot... more than 10 installs for myself.

HOWEVER... 
My nephew didn't quite understand the partitioning options and selected "Guided use entire disk."
By doing so, he had instructed the installer to WIPE out windows and install ONLY ubuntu to the 
machine... so pay especial attention to that portion of your install and all should go well.

-WebDr

---

### Post by erginemr on 2007-12-04
Hello,

In addition to all above comments, you can also read the following guide to familiarize yourself with the installation steps:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The most important thing is to be careful to not erase your Windows partition by mistake. Other than that, installation is piece of cake. You need to defragment your Windows drive before the installation, and resize it during the installation to give Ubuntu some space. 

You will need a minimum of 5 GB (10 - 20 GB recommended) for the EXT3 root partition and 2 times your RAM (say 1 GB if you have 512 MB RAM) for the SWAP partition. Some prefer creating another one for the /home directory, but then again, for your first experience, I believe you should not complicate things for you.

First you should run the Live CD to make sure that all your peripherials. or rather the ones you cannot live without (such as network card, Internet access, printer, scanner, webcam, etc.) work in the Live CD environment. Also make sure that your graphic and sound cards are well supported under Linux. 

If you do not like using Ubuntu later on (which is highly unlikely, because people running dual-boot usually end up with leaving Windows altogether and continue with using Linux only), you do not need to worry at all. Uninstallation requires taking a few simple steps, I am sure you will be able to find lots of information on the subject, when the time comes (hopefully never).

Have Fun with Ubuntu!

---

### Post by louieb on 2007-12-04
> **Actuary32174 said:**
> ,,,Currently, XP is running on my computer. If I attempt to install ubuntu on the computer and something goes wrong, how difficult is it to totally remove the program from the computer?,,

Depends  on how your equipped to  deal with disaster. 
If you have good backup and know how to restore your hard drive  - its easy. 
No backup? No XP install CD? Not computer savvy?  Its a long hard task - maybe impossible to  restore.

Setting up a PC to dual boot is not like installing Pinball Arcade in windows. You have to alter some very important parts of your hard drive. The process is straight forward and is done without a problem most of the time.  [B]But:
[/B] Remember Murphy's Law?  - "whatever can go wrong, will go wrong."

---

### Post by erginemr on 2007-12-04
> **louieb said:**
> Depends  on how your equipped to  deal with disaster. 
If you have good backup and know how to restore your hard drive  - its easy. 
No backup? No XP install CD? Not computer savvy?  Its a long hard task - maybe impossible to  restore.

Setting up a PC to dual boot is not like installing Pinball Arcade in windows. You have to alter some very important parts of your hard drive. The process is straight forward and is done without a problem most of the time.  [B]But:
[/B] Remember Murphy's Law?  - "whatever can go wrong, will go wrong."

With all due respect, I do not agree. If I were a newbie reading your post, I would turn on my heels and run away from Ubuntu or Linux as fast as I could. I can understand that you want him to comprehend the risks involved, but we should not scare away newcomers this way.  

Most people who are using Ubuntu, have installed it with dual-boot at the beginning. Once you get past the partitioning process, all configuration for the dual boot is made automatically by the Ubuntu installer. (Small adjustments if required, can be made later on.) Although admittedly, installing an operating system has never been a child's play, I also believe that with a good bit of reading before actual installation, anyone can easily install Ubuntu.

So, my advice to Actuary32174 is to get his feet wet and install Ubuntu.

---

### Post by V3M4 on 2007-12-04
> **erginemr said:**
> With all due respect, I do not agree. If I were a newbie reading your post, I would turn on my heels and run away from Ubuntu or Linux as fast as I could. I can understand that you want him to comprehend the risks involved, but we should not scare away newcomers this way.  

Most people who are using Ubuntu, have installed it with dual-boot at the beginning. Once you get past the partitioning process, all configuration for the dual boot is made automatically by the Ubuntu installer. (Small adjustments if required, can be made later on.) Although admittedly, installing an operating system has never been a child's play, I also believe that with a good bit of reading before actual installation, anyone can easily install Ubuntu.

So, my advice to Actuary32174 is to get his feet wet and install Ubuntu.

I am a noob and I don't think the advice was bad at all. In fact, I think it's better to tell someone that's about to try and dual boot over a working XP install of the pitfalls than to encourage them to jump right in and end up having to wipe everything and start from scratch. I've been running on Ubuntu for a month now and am in total love, it was worth the risk, and the installer and partition manager were out of site, making it close to a no brainer to keep my existing xp install in tact, but the risk of accidentally overwriting my xp install was very real. Backup!

---

