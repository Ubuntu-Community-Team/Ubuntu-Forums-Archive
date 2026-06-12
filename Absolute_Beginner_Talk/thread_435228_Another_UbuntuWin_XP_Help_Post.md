---
title: "Another Ubuntu/Win XP Help Post"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by johndale on 2007-05-06
Hey Folks,

I've been reading the posts here and have appreciated all the great information. Thank you to all.

I'm BRAND NEW to Linux and still am trying to get my head around the install and use. So I have a couple of questions...

**Item One: The different Versions of Ubuntu**

I see people referring to Feisty Fawn and other Names - which I think are just Names for the different builds of Ubuntu. And version 7.04 is named Feisty Fawn. Is that right?

**Item Two: Why Ubuntu vs. other Flavors of Linux?**

Why are you all installing Ubuntu vs. other versions of Linux like Knoppix, Red Hat? (those are the only two of which I've really ever heard)

**Item Three: Re-Partitioning Your Win XP Install**

I've booted from the Ubuntu 7.04 CD and clicked on the "install" desktop icon and gotten as far as the screen where you can repartition your drive -- and stopped because I wanted to ask these questions. It looks like in version 7.04 you don't need things like QtParted because it's built into the installation. In other words the 7.04 spoon feeds it to me because I'm nervous about hosing my Win XP install.

**Item Four: Why the Shared FAT32 partition?**

It looks like you can add some additional stuff to your Ubuntu and Win XP installs and so that each can read/write on the other's partitions. If that's true, why do you need a FAT32 "shared" space and can't you just have the NTFS, EXT3 and Linux Swap partitions?

**Item Five: Will I Hose My XP Install?**

Even though I'll have a complete backup before proceeding, I'd love to avoid hosing my Win XP Install. How likely is it that all will go smooth? And in an hour after starting I'll be a new happy convert to the non-MS life?

**Item Last: Boot loaders?**

I've read here that there's a Linux boot loader that people use called Grub (not sure about the name). And then other people use the Win XP boot loader. Which one should I use and why? And even more important, how do I make all that work?


Thank you SO MUCH in advance

John

---

### Post by the lemming on 2007-05-06
> **johndale said:**
> 
**Item Five: Will I Hose My XP Install?**

Even though I'll have a complete backup before proceeding, I'd love to avoid hosing my Win XP Install. How likely is it that all will go smooth? And in an hour after starting I'll be a new happy convert to the non-MS life?



I have been trying to install 7.04 since 9am and I have lost count how many times I have lost XP as well today.  At the moment Ghost is putting XP back onto my computer for yet another try.

I hope you have more sucess than me.

Good luck

---

### Post by bobplano on 2007-05-06
1. yep those names like dapper drake, edgy eft, and fiesty fawn are  the newer released versions of ubuntu. feisty is the newest, but still has some bugs as far as i'm aware. 
2. there isn't one reason why all of us installed ubuntu over everthing else. some people here use soley or dual-boot with other linux flavors, so not all of us here are just ubuntu. 
3. as long as you don't use the delete feature of resize your XP partiton to an extrememly small amount it acutally isnt that easy to destroy your windows. 
4. having a fat32 shared partition just makes it easier for both OSes. linux can use ntfs3g and windows can use exf2s or something, but why set one more thing up that could break(unlikely but still)?
5. most installations will go fine as long as your cd is error-free. 
6. GRUB is the default bootloader for ubuntu. i havent used the windows one, but it should detect your XP partition right away. if it doesn't you will have to add one by editing your grub files(worry about that later because most of the time it should detect it)

---

### Post by Tenicus on 2007-05-06
> **johndale said:**
> Hey Folks,

I've been reading the posts here and have appreciated all the great information. Thank you to all.

I'm BRAND NEW to Linux and still am trying to get my head around the install and use. So I have a couple of questions...

**Item One: The different Versions of Ubuntu**

I see people referring to Feisty Fawn and other Names - which I think are just Names for the different builds of Ubuntu. And version 7.04 is named Feisty Fawn. Is that right?
Right exactly
[B]7.04 = Fiesty 
6.10 = Edgy 
6.06 = Dapper
[/B]
**Item Two: Why Ubuntu vs. other Flavors of Linux?**

Why are you all installing Ubuntu vs. other versions of Linux like Knoppix, Red Hat? (those are the only two of which I've really ever heard)
**I just like Debian based distros (Ubuntu is one), particularly the simplicity and power of the apt-get system.  Everyone has different reasons, some people prefer Red Hat.  Knoppix is a Live CD, I dont know if its installable.**
**Item Three: Re-Partitioning Your Win XP Install**

I've booted from the Ubuntu 7.04 CD and clicked on the "install" desktop icon and gotten as far as the screen where you can repartition your drive -- and stopped because I wanted to ask these questions. It looks like in version 7.04 you don't need things like QtParted because it's built into the installation. In other words the 7.04 spoon feeds it to me because I'm nervous about hosing my Win XP install.
**I dont get this, but essentially you should think about doing a back up of your XP data in case anything goes wrong.**
**Item Four: Why the Shared FAT32 partition?**

It looks like you can add some additional stuff to your Ubuntu and Win XP installs and so that each can read/write on the other's partitions. If that's true, why do you need a FAT32 "shared" space and can't you just have the NTFS, EXT3 and Linux Swap partitions?
**I know that linux can read and write to NTFS but there is a very little, but still possible, chance of  it damaging the NTFS drive.  FAT32 is safer.  I use NTFS though.**
**Item Five: Will I Hose My XP Install?**

Even though I'll have a complete backup before proceeding, I'd love to avoid hosing my Win XP Install. How likely is it that all will go smooth? And in an hour after starting I'll be a new happy convert to the non-MS life?
[B]Unless you tell it to install over the XP partition, it should be fine. 
Also, unless you are a hardcore gamer, I cant think of why you would dislike ubuntu.[/B]
**Item Last: Boot loaders?**

I've read here that there's a Linux boot loader that people use called Grub (not sure about the name). And then other people use the Win XP boot loader. Which one should I use and why? And even more important, how do I make all that work?

**Dont worry about this, when you install ubuntu it well set it up for you.**
Thank you SO MUCH in advance

John
Good Luck

---

### Post by Nekiruhs on 2007-05-06
AS far as boot loaders go, I would recommend using GRUB , the default Ubuntu boot loader.  IT is far more configurable that the Windows one.

---

### Post by rygar on 2007-05-06
1) You are correct, sir!

2) Everyone has their own reasons, and I'm sure no linux distribution is right for anyone.  I chose Ubuntu because it seems to have great support and it seems to be the distribution catered best to non-gurus...  We've got to get eased into linux somehow!

3) Correct--Feisty Fawn, aka 7.04 does not require you to use any other partition software, presuming things go well.  It's built right into the installer.

4) You don't!  I don't have a FAT32 partition on my system.  I can read/write to my linux and windows partitions from either OS.  However, both need some extra software to get this done.  In Windows, you need to download software even just to read your linux partition.  In Ubuntu, you need to install some software to be able to modify your windows partition from linux.

5) You did the the smart thing with backing up.  If you follow the automatic installation, things will probably go smoothly.  You most likely want to choose the option to install on the "largest continuous free space".  If you only see options for "Use entire disk", come running back here for help and someone will be there.  Better yet, do a search on the forum and you'll find a bunch of threads on the forum that already guide you around this problem.

6) In my opinion, which boot loader you use is irrelevant if it works correctly.  I've heard the windows boot loader sometimes has problems loading Ubuntu.  Luckily, in your case, GRUB will be the default boot manager since you installed Ubuntu after XP.  Ubuntu should detect your Windows installation automatically, and you shouldn't have to do anything.  Again, if for some reason GRUB does NOT load itself with your installation, come back here and someone will be here to help.

Hope this helps, and welcome to Ubuntu!

---

### Post by johndale on 2007-05-06
Can I just say this place is AWESOME!

I posted a long-*** message 30 minutes ago and I've already gotten a ton of replies. 

Thank you. Thank you! Very helpful information.

---

### Post by alienexplorers on 2007-05-07
When installing Ubuntu try to make 3 partitions 1 for ROOT (/), 1 for HOME (/home), and a small (1 to 3GB) for swap.

This way your preferences for the various programs are stored on /home and if you ever need to re-install Ubuntu you just need to re-install the root section leaving your preferences unchanged.

I have had to re-install and this beats having to re-setup everything all over again.

---

