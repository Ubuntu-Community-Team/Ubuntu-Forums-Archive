---
title: "Hellish time trying to install Xubuntu 7.04"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by el profe on 2007-08-03
I have been on the computer for just about 18 hours(with 5 hours sleep) trying to install xubuntu 7.04 and Ive just run into problems after problems, gone through manuals, google, launchpad and forum search but still problems keep on pilling up so I came here. Here is the rundown:

I am installing on a vaio, xp 1.5 GHZ, 256 ram. All the info on this computer was moved to another so there are not files to lose, but I do want the option to dualboot.

I am installing with livecd and when I first tried installing I got stuck on step 4 partitioning. I went into manual partition, leaving the 15 gigs fat32 drive alone but wanting to split the 40 gig NTFS into two, firt it gave me an error and then it didnt get out of the edit box, I was going to try the fix suggested in the release notes but I couldn't find applications and like I said I couldnt even get out of the edit partition box.
Something weird did happen even though I got a "cant partition" error the partition type changed to ext 3, the whole partition.
I went looking for answers on launchpad and was told to try Gparted, so I did and split the 40 gigs intoa NTFS and ext3 partition. Checked it on windows and it was split.

Next I tried reinstalling linux and tried again manual partition, it didnt work, so I went with automatic partition and chose to partition the whole drive, thinking it was partitioning the ext3 drive. So I went through that got and openoffice error while installation nothing major though because it finished installing xubuntu.

I restarted my pc and first thing I noticed was that it did not give me the option to choose a OS it went str8 into xubuntu(ive restarted the pc a couple of times already and same thing happens) when I tried to log in I got a this message:
**GDM could not write your authorization file . This could mean that you are out of disk space or that your home directory could not be opened for writing . In any case it is not possible to login. Contact system administrator**. 
Ive been on the internet searching for answers and trying different "fixes"(including a couple in this forum) but none seem to work, it is also strange that I would get this message since I just isntalled the os. OH btw, anyone know how to type "|" in linux, I cant seems to type it in there, I tried shift+\, then alt+124, but cant that typed in. 
Anyway I have spent more time looking for answers than on the pc itself and its just frustrating. Now I will have to reformat the pc, reinstall windows and then try to install xubuntu again but I just dont want to run into all the problems I have encountered so any help is appreciated...

Thanks

ps. needless to say I am a linux noob, this was my first time installing it.

---

### Post by Rocket2DMn on 2007-08-03
Have you tried the alternate install cd?  It gives a text based installation and tends to prevent a lot of problems that otherwise tend to popup with the live cd.
[http://www.xubuntu.org/get](http://www.xubuntu.org/get) - select your region and choose a mirror, and select the alternate instead of desktop iso.
Once the .iso is downloadd, check the md5sum
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("http://mirror.anl.gov/pub/ubuntu-iso/DVDs/xubuntu/7.04/release/MD5SUMS") to check against
Once that checks out, you can burn the iso to a cd at a slow speed, like 4x, to prevent write errors, and use quality media if possible.

Now you shouild install windows first, should wipe the drive using with windows install, and partition it so windows uses however much you want, leaving the rest for xubuntu unpartitioned.  After the windows install, boot from the xubuntu alternate cd and proceed to install - remember you need space for SWAP.  GRUB should be installed as well which should automatically detect windows and give you the option to boot to that OS as well as xubuntu.  Assuming the install goes well, if for whatever reason windows is not an option at the GRUB boot menu, we can troubleshoot that without having to reinstall anything.
Good luck.

---

### Post by spur on 2007-08-03
As you only have 256ram I think you would be  better off with the 'alternate cd' for installation rather than the 'live cd' as it uses lessram because it does not have to use the cd as an os while installing.
The cd is downloadable from the Ubuntu web site [http://www.ubuntu.com/]("http://www.ubuntu.com/")
This site has some usefull info on partitioning for Ubuntu and windows as well. [http://psychocats.net/ubuntu/partitioning]("http://psychocats.net/ubuntu/partitioning")

---

### Post by ReaderRat on 2007-08-03
[Partitioning Basics](http://ubuntuforums.org/showthread.php?&t=282018)

Dual-Boot, ALT CD Install, XP:[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by ARandomKid on 2007-08-03
> **spur said:**
> As you only have 256ram I think you would be  better off with the 'alternate cd' for installation rather than the 'live cd' as it uses lessram because it does not have to use the cd as an os while installing.
The cd is downloadable from the Ubuntu web site [http://www.ubuntu.com/]("http://www.ubuntu.com/")
This site has some usefull info on partitioning for Ubuntu and windows as well. [http://psychocats.net/ubuntu/partitioning]("http://psychocats.net/ubuntu/partitioning")

Actually, the live CD worked fine for me and I only have 123MB RAM...

but then, I wasn't trying to do all this stuff, just install Xubuntu...

---

### Post by el profe on 2007-08-03
> **ReaderRat said:**
> [Partitioning Basics](http://ubuntuforums.org/showthread.php?&t=282018)

Dual-Boot, ALT CD Install, XP:[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

IN the partitioning basics it says to create a ext3 partition and swap partition, I was under the impression that automatic partitioning does this? if its not tha tcould of been my mistake the first time. If its not then do I leave x amount of space left for the automatic partitioning to partition a swap drive?

btw what is a swap drive? lol

---

### Post by splintercellguy on 2007-08-03
Automatic should do that. As for what a "swap drive" is, it is basically an extra buffer in case an application requires more memory than you have physically installed. Disk access is obviously slower than memory, so it's very much preferred to have more memory.

---

### Post by jerrynewt on 2007-08-03
the "|" is the uppercase \

---

### Post by el profe on 2007-08-04
I went ahead with the reinstall and decided to boot gparted just to clear the partitions, to my surprise windows was still there so I just cleared the xubuntu partition, and tried installing with the livecd but this time on a unformatted partition, I installed wihtout problems and it is up and working right now, the only questin I have is 3 disk or folders appear, file system, 21 gb and 16, I can only access system the other 2 can only be accessed by the administrator with password, I imagine this iis adefault setting because there is no"administrator", anyone know what the purpose of this is and what the password (is it my regular login password?).

Ill start reading up on the manuals for using xubuntu tomorrow :-| ,lol

---

### Post by ugm6hr on 2007-08-04
> **el profe said:**
> I went ahead with the reinstall and decided to boot gparted just to clear the partitions, to my surprise windows was still there so I just cleared the xubuntu partition, and tried installing with the livecd but this time on a unformatted partition, I installed wihtout problems and it is up and working right now, the only questin I have is 3 disk or folders appear, file system, 21 gb and 16, I can only access system the other 2 can only be accessed by the administrator with password, I imagine this iis adefault setting because there is no"administrator", anyone know what the purpose of this is and what the password (is it my regular login password?).

Ill start reading up on the manuals for using xubuntu tomorrow :-| ,lol

Yes - it's your password - you are the administrator!

This will help you to auto-mount everything at startup (if you want):
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mig5 on 2007-08-04
Root password is the first password that you put in when you made the original user in the installation.  Those two extra disks are probably your Windows partitions (at one will be, do you have two Windows partitions?).
To run the filemanager as root to access those partitions go to a terminal and type:
```
gksu thunar
```
You should then be prompted for your password (note the password you type in here is the password of your user account, in Ubuntu users request root access rights with gksu and sudo commands, and therefore they are asked for the password of the user who is running the command, which is not necessarily the root one).

---

### Post by el profe on 2007-08-04
> **ugm6hr said:**
> Yes - it's your password - you are the administrator!

This will help you to auto-mount everything at startup (if you want):
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

what do you mean auto-mount everything at startup? what exactly would this do?

thanks

---

### Post by ugm6hr on 2007-08-04
> **el profe said:**
> what do you mean auto-mount everything at startup? what exactly would this do?


"Mounting" is what you do if you want to access a partition / device.  As default - in Ubuntu - your root partition (**/**) is mounted at startup, and any *external* (e.g. USB etc) drives are mounted when plugged in.

You can have any internal drive be mounted at startup - the links provide details to do this.  They will also ensure that you will not need a password each time you want to access the drives.

Using *gksu thunar* is not the best option for 3 reasons:
1. you will have to enter this every time you want to access the drive.
2. you will have to enter a password every thime
3. if you accidentally access your root drive from this control and move or delete important files (which can happen with a slip of the mouse) - you can potentially ruin your installtion.

Therefore, *gksu thunar* should be reserved for when you *need* to edit system files (carefully).

So - my suggestion is to have them accessible in read-write for you when you boot up.  Unless you will never need to access them from Ubuntu.

---

