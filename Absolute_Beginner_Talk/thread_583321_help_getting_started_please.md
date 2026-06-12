---
title: "help getting started please"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by XXBen on 2007-10-20
Hi, i'm new to ubuntu and have read many posts with people having this same problem, however, there never seems to be a very straight answer to the question. This is what i need to do.

I need to be able to view files on my secondary drive. I have a 300gb hard drive that I use for storage and when i try to view it, i get a message that say's" Unable to mount the selected volume." So therefore i cant view my files that are on that drive.

Here is what i get when i do this command from a terminal "sudo fdisk -l"

/////////////////////////////////////////////////////////////////////
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19089   153332361   83  Linux
/dev/sda2           19090       19457     2955960    5  Extended
/dev/sda5           19090       19457     2955928+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS
ben@Ben:~$
ben@Ben:~$
//////////////////////////////////////////////////////////////

How do i access my files in the 300.0GB hard drive?

Also, I need to install Xfire, its a gamming chat program that i use frequently, I used it with windows but i cant instsall it, How do I install that program and all my games? (Battlefield 1942, Battlefield 2142, Microsoft Halo,) and others like this????
Please help me do this, i'm likeing Ubuntu alot so far for how simple and smooth it operates, but I need my programs in staled and need to be able to access my files on my storage drive. Please write your response in very easy to understand detailed instructions as i have no idea really how to do anything with ubuntu yet, Thanks.
Ben

---

### Post by Linux_Man on 2007-10-20
Well, there should be a way to view your secondary hard drive (Don't know the commands right off the top of my head though) As for Games, your best bet is to dual boot Windows and use that, you can try Wine but not everything works perfectly and if your a hard-core gamer, until game companies support Linux you will probably be stuck with Windows, try Wine though

---

### Post by Linux_Man on 2007-10-20
I found what you need to do


[http://ubuntuforums.org/showpost.php?p=3580117&postcount=2](http://ubuntuforums.org/showpost.php?p=3580117&postcount=2)


That should get your NTFS hard drive working

---

### Post by XXBen on 2007-10-20
I suppose i'm supposed to run those commands from a Terminal? well i did and this is what i get:
ben@Ben:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config
Again, i am a brand new beginner, if you give me some commands, please tell me how and where to use them, thanks for the help but nothing working yet.

I thought Linux was designed for hard core gammers? Someone told me this once. Where do I get this Wine?

---

### Post by Maestro23 on 2007-10-20
> **XXBen said:**
> I suppose i'm supposed to run those commands from a Terminal? well i did and this is what i get:
ben@Ben:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-config
Again, i am a brand new beginner, if you give me some commands, please tell me how and where to use them, thanks for the help but nothing working yet.

I thought Linux was designed for hard core gammers? Someone told me this once. Where do I get this Wine?

Make sure your universe and multiverse repo's are enabled.  System>> Admin>> Software Sources

Then run the command again.

As for you Windows games, they are not going to run under linux.  You will need a program line Wine or Cedega.

WineHQ: [http://www.winehq.org/](http://www.winehq.org/) (Wine is available thru Synaptic).

Cedega: [http://www.transgaming.com/](http://www.transgaming.com/)

*I'm a heavy gamer myself, that is why I dual boot with XP.  The ONLY reason XP is on my system.

---

### Post by XXBen on 2007-10-20
Are there any other Free OS's out there that do support gamming? Is there a way to install programs like Xfire in linux?

---

### Post by ryanVickers on 2007-10-20
Xfire worked for me in wine and CXoffice, but it was the combination of having it installed that I got it to work :p

some things worked in one, some in the other..., mostly cxoffice though...

---

### Post by medicineman24 on 2007-10-20
They all support gaming although Windows will make the best use of your hardware when gaming.  Plus most commercial games are designed for windows.

---

### Post by XXBen on 2007-10-20
wOW, These two links you gave me led me to some web sites with a bunch of jibberish talk, i could not find how to download either of them, the wine site said something about entering some codes? is that all i need to do? just enter the codes in any old terminal? or do i actually need to download whine? it would be nice if someone could put a direct link to download wine in this thread. Is everyone this confused with linux when they fist start? I just want to click on the file and watch it install. wtf.

---

### Post by lyndaj70 on 2007-10-20
Install Automatix2. It has a plugin that will let you mount the drive and use it.... You can find it and download/install instructions at [www.getautomatix.com](www.getautomatix.com).  That's what  I used to fix the problem.  Hope it helps....
~L

---

### Post by ryanVickers on 2007-10-20
I have only received good service with no problems from it, but I would not recommend it actually ;)

that being said, my signature will provide the absolute simplest and flawless way ;)

---

### Post by XXBen on 2007-10-20
Thanks, i'll try that. so far, the only thing i can do is browse the internet with this ubuntu linux. why do people want to use it? I cant even go to pokerstars.com and download the program to play poker??? what is so great about this linux? Mabe i should just stay away from it? It seems so difficult.

---

### Post by XXBen on 2007-10-20
Wow, i'm really starting to feel dumb now, I could not find a download link anywhere for the automatix, help please...

---

### Post by Duck2006 on 2007-10-20
> **XXBen said:**
> Thanks, i'll try that. so far, the only thing i can do is browse the internet with this ubuntu linux. why do people want to use it? I cant even go to pokerstars.com and download the program to play poker??? what is so great about this linux? Mabe i should just stay away from it? It seems so difficult.

Because those sites mainly use IE.

---

### Post by Natr0n on 2007-10-20
wine
system->administration->synaptic package manager
enter password
click search
type "wine" (without the quotes)
hit enter
check the box next to wine (if extra packages are needed allow them)
click apply

ntfs read/write
system->administration->synaptic package manager
enter password
click search
type "ntfs-3g" (without the quotes)
hit enter
check the box next to ntfs-3g (if extra packages are needed allow them)
click apply

Please post any problems you have with these instructions.

---

### Post by XXBen on 2007-10-20
-Nathan, Problems with those instructrions:

First, thank you for the walk thrgouh, you made it easy for me to do this.

Problem: the search produced no results, there were no packages to select. any more helP? Thanks
Ben

---

### Post by Frak on 2007-10-20
> **XXBen said:**
> Are there any other Free OS's out there that do support gamming? Is there a way to install programs like Xfire in linux?
Some games will work, but some to most will not. They are slowly porting Games to Linux (I mean SLOWLY), but until then its always good to have a Windows partition.

---

### Post by Maestro23 on 2007-10-20
> **XXBen said:**
> -Nathan, Problems with those instructrions:

First, thank you for the walk thrgouh, you made it easy for me to do this.

Problem: the search produced no results, there were no packages to select. any more helP? Thanks
Ben

Need to enable your Universe and Multiverse Repo's.  System>> Admin>> Software Sources

*Then try those packages again.

*If you are a gamer, then I would suggest you dual-boot with XP.  Gaming is the only thing that keeps XP on my system.

---

### Post by XXBen on 2007-10-20
but i've never downloaded those packages, does that matter??? I dont konw why i'm not getting this, I am a php scripter, I know windows in and out, I just dont understand this linux

when i go to System/Admin i only see software properties no software sources, I have ubuntu 6.06 lts do I need a diferent version?

---

### Post by Natr0n on 2007-10-20
Which version of ubuntu are you using?
Did that happen for both packages?
I suspect you simply need to enable the correct software sources but the instructions differ slightly depending on which version you're using.

EDIT: Yeah, what Maestro23 said. Also, make sure to search in "description and name" as that will likely yield the most results.

---

### Post by Frak on 2007-10-20
OK, from now on, something you'll need to know

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Linux is not something you learn overnight, it takes some time to get used to, but unless your job requires it, you'll come to like Ubuntu in the long run. It will teach very much about the in's and out's of how a computer works and show you the importance of OSS, including the sharing and security of it.

---

### Post by XXBen on 2007-10-20
Ok, I now have Ubuntu 7.10 and some of the commands are working, I installed ntfs config and ran the command, "ntfs config" tried mounting the drive and this is what i get, any suggestions?



/////////////////////////////////
 Mounting /media/Storage failed.

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Storage -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Storage ntfs-3g defaults,force 0 0
/////////////////////////////////

---

### Post by ryanVickers on 2007-10-21
It looks like it thinks it was unmounted uncleanly, whether this was an improper remove, or a power-off without a proper shutdown...

Try going back to the drive under windows and shutting down properly (if this really *is* the problem ;))

---

### Post by Maestro23 on 2007-10-21
> **ryanVickers said:**
> It looks like it thinks it was unmounted uncleanly, whether this was an improper remove, or a power-off without a proper shutdown...

Try going back to the drive under windows and shutting down properly (if this really *is* the problem ;))

Getting ready to suggest the same thing.  Happened to me once when XP crashed on me and a rebooted into Ubuntu.

---

### Post by ryanVickers on 2007-10-21
while we're on this note, I'd like to say that this one time there was a power outage when on XP - I was not using the disk or anything, and it was NTFS, and when I rebooted, it was corrupt.  Nothing could fix it "1 or more unrecoverable errors were encountered" it said ;)

I booted to Linux (which at the time was still my secondary OS) and it was able to read everything perfectly.  I don't remember *exactly* how, but I saved everything because of course, Linux could read it fine! :)

Since then, I've used Ubuntu! :D

Through many power outages with out a problem I might add ;)

---

### Post by Frak on 2007-10-21
Do you hear a drive tick?

---

### Post by XXBen on 2007-10-21
no, i dont hear a drive tick, also, the dirve no longer shows up in my Places/computer, I dont have windows installed anymore, i replaced my windows installation with ubuntu, i just assumed that linux would read my secondary drive with no problems. all my files are on my secondary drive. this is a seperate physical drive 300 GB of memory, all the pictures of my kids growing up and basically everything. do i need to install a second OS of windows to access those files? surely linux can read the drive. Please help me. I have exausted myself searching the furms and it seems many many people have this problem, some of them fix it but i have not been able to find a clear, easy fix. can someone explain in lame mans terms please?

---

### Post by XXBen on 2007-10-21
any help?

---

### Post by Natr0n on 2007-10-21
Have you tried this```
mount -t ntfs-3g /dev/sdb1 /media/'DRIVENAME' -o force
```yet?

---

### Post by XXBen on 2007-10-22
It say's only root can do that. What do i need to do now? is there a way to log in as root? And do i specify a drive name or does that have to be specific? cause i dont even see the drive in Places---> Computer

---

### Post by Maestro23 on 2007-10-22
> **XXBen said:**
> It say's only root can do that. What do i need to do now? is there a way to log in as root? And do i specify a drive name or does that have to be specific? cause i dont even see the drive in Places---> Computer

Need **sudo** in front of your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

