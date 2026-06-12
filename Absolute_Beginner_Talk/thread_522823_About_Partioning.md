---
title: "About Partioning"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-11
I am a total newbie in the Ubunt Linux world.
This is my PCs Congfiguration:
User: Administrator
Operating System: Microsoft Windows XP Professional 5.01.2600 Service Pack 2
Report Date: Friday 10 August 2007 at 13:54
System Summary
Mainboard Intel D915GAV
Chipset Intel i915G
Processor Intel Pentium 4 530J @ 3000 MHz
Physical Memory 1024 MB (2 x 512 DDR-SDRAM )
Video Card ATI Technologies Inc Radeon X1650 Series
TV Tuner AVerTV GO 007 FM Plus
Hard Disk HDS728080PLA380 (82 GB)
DVD-Rom Drive SONY CD-RW CRX300E
DVD-Rom Drive ASUS DVD-E616A3
Monitor Type LG Electronics E700SH - 17 inches
Network Card Realtek Semiconductor RT8139 (A/B/C/810x/813x/C+) Fast Ethernet Adapter
Operating System Microsoft Windows XP Professional 5.01.2600 Service Pack 2
DirectX Version 9.0c (July 2007)

Yesterday I posted a message but i didn't got one answer and i have a few more questions.

I have 5 partitions(C:Windows , D:Mixed ,E:Vids , F:Music, G:Games,) .Each partition has 15.33Gb of space .Now my G:Partition/Drive is empty.First  i want to try Ubuntu with Windows XP on a dual-boot system.

Please answer my questions in detail.

1)If i delete the G: Partition will i be able to install Ubuntu 7.04 on it?
2)If i want to use Ubuntu fully discarding Windows XP , can i have 5 partitions like the way i have in windows?
3)After few months i Quick Format my C:Partition on which WindowsXP is installed and Clean install Windows. Can i do the same with Ubuntu if yes please tell me the process.
4)I download all my files(music,videos,documents,archives) on D: Partition cause i format my C: Partiton. 
Can i backup all the softwares ,Libraries, Drivers in another drive on Ubuntu if Yes then How & where are the files located after Ubuntu downloads them.

Plaease answer these questions in detail.

---

### Post by sad_iq on 2007-08-11
oK...Here goes...first of all...forget all you know about Windows to be able to understand how any linux distribution works...so my answers woun't make much sense at the beginning:
 1. If the G:\ partition is a primary one...yes, if it is a logical one you could install ubuntu in the C:\ drive shrinking it's size.
 2. Linux doesn't use partitions like windows, the filesystem is different, the equivalent of the C:\ drive is **/** in linux(called the root of the drive), everything is set below it. Read this and google some more to understand the linux filesysytem:[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
 3. Yes...however that will not be necessary as you won't see the slowdowns as you see them in Windows. Linux is different remember!!! Anyway you can do it is you want, just install ubuntu again, and if you create a separate /home partition do not format it!!!
 4. Ubuntu(Linux) doesn't download drivers like you do with Windows(ussualy), so to see if ubuntu works on your hardware just download the LiveCd and run it, you'll see the network working out of the box, sound...and hopfully more things. Anyway the best backup is to have a separate /home partition witch will store all your preferences and music and all!!!
 Can't really give more detailed instructions at the moment, let's see if somebody will, but if you have more questions please post them here!!!

---

### Post by rubab on 2007-08-11
Thanks sad_iq

Waiting for more replies.

I have 0 experience about programming. As i am willing to use Ubuntu Fully , which programming language should i start with?

I still didn't understand the way Ubuntu Linux file system works and about formatting(See the 1st questions)

Which is the best File System for Ubuntu(Now i am talking about ext3 and other File systems)

---

### Post by MenZa on 2007-08-11
> **rubab said:**
> 
I have 0 experience about programming. As i am willing to use Ubuntu Fully , which programming language should i start with?


Well, you could start by learning shell scripting in Bash; it's often incredibly useful for performing simple tasks on your system. If not, there's either Perl or Python (or PHP).

> **rubab said:**
> 
Which is the best File System for Ubuntu(Now i am talking about ext3 and other File systems)


There's so many to choose from; I think I'd just go for ext3 if I were you.

---

### Post by sad_iq on 2007-08-11
> I have 0 experience about programming. As i am willing to use Ubuntu Fully , which programming language should i start with?
So...what makes you think that you need to be a programmer to use ubuntu(or linux for that matter)?? I studied a little bit of programming a few years ago...but i never used it in Ubuntu. All you need to learn is a few commands to write in a terminal if you ever need to use them!!!
 About partitioning...Ubuntu will require out of the box a minimum of 2 partitions the root partition **/** (equivalent of the C:\ drive in Windows) and another partition for swap. Also it's a good idea to have a separate **/home** partition (more or less the equivalent of the D:\ drive), where all your settins and data will be stored. If the G:\ partition is not a primary partition you cannot boot Ubuntu and you cannot create the swap and /home partitions. The best thing you can do is download the LiveCd and run with it for a little while...that should give you an idea of how Ubuntu works, and it will give us some details about the partitions and the type of partitions you have if needed.
 Also...i googled an image...that will give you a better view of the linux dyrectory structure...notice the / is at the top...everything else is below...so even a different partition will be below **/** (**/home** will be the same in a separate partition)
[http://www.powys.lug.org.uk/images/filesystem.jpg](http://www.powys.lug.org.uk/images/filesystem.jpg)

---

### Post by chadwicktr on 2007-08-15
I've just started using ubuntu this summer. WHen you say /home stores all of your settings, what do you mean by that exactly? Is this something to do with all of the ".folders" -- i guess a Windows analogy would be the .folders are hidden?

---

### Post by chadwicktr on 2007-08-15
Also, I've installed ubuntu with only one partition plus the swap. Do I have to do a fresh install to move my /home folder to a different partition?

Also, does the home folder store all the info of my desktop? I setup my computer with the default gnome, but it ran a litlte slow on my older hardware so I installed the Xfce (xubuntu) desktop and use that now. Is htat data stored in my home folder?

---

### Post by Hobo Joe on 2007-08-15
> **rubab said:**
> 
Please answer my questions in detail.

1)If i delete the G: Partition will i be able to install Ubuntu 7.04 on it?
2)If i want to use Ubuntu fully discarding Windows XP , can i have 5 partitions like the way i have in windows?
3)After few months i Quick Format my C:Partition on which WindowsXP is installed and Clean install Windows. Can i do the same with Ubuntu if yes please tell me the process.
4)I download all my files(music,videos,documents,archives) on D: Partition cause i format my C: Partiton. 
Can i backup all the softwares ,Libraries, Drivers in another drive on Ubuntu if Yes then How & where are the files located after Ubuntu downloads them.

Plaease answer these questions in detail.

1. Yes, and no. The max number of partitions on a harddrive is 5, which you already have, and Linux needs 2, preferably 3. So in other words you will have to delete two of them, or three.

2. Yes, but I wouldn't recommend it. I Linux it's better to have 1 partition for the operating system, and the other for your /home folder(all your program configurations and personal files)

3. Yes you can, but you don't need to. Ubuntu doesn't get clogged up like Windows does.

4. Like I said on question 2, if you ahve a separate /home partition than you don't need to worry about that, when you re-install, it won't format, and you'll start up with ALL The same files and program configurations that you had before re-install. But, like I said, you won't need to re-install ubuntu like you did with Windows.

---

### Post by Chaotic Thought on 2007-08-16
> **Hobo Joe said:**
> The max number of partitions on a harddrive is 5, which you already have, and Linux needs 2, preferably 3.
The max partitions is actually 4 physical partitions, and of those physical partitions, what you normally do nowadays is make one of those an "extended partition" and then make as many logical partitions as you want inside it. Windows might complain if it is installed in an extended partition, but Linux is totally OK with it.

Also, Linux doesn't "need" 2 partitions. I understand people like to have separate partitions for swap and home, but if you want to do it with just 1 partition, that is totally cool in Linux also. You can assign a flat file on your install partition as the swap device.

---

### Post by daveshields on 2007-08-16
rubab,

The hardware/software details of your system don't matter. The essential details are that 
1) you admit you are new to Ubuntu
2) you have software, including a copy of Windows that you paid for and probably other programs as well, and -- more importantly -- data that is important to you.

The net of this is that you don't even want to attempt to install Ubuntu on a computer until you have confidence in what you are doing, or don't care if the existing contents of the hard disk are lost.

Hard disks are cheap. Ubuntu needs less than 10GB so any hard disk should work. Substitute that disk for your current disk. The default install will use the entire disk. Install ubuntu and play with it for a bit.

 Once you have Ubuntu installed you can start to have some fun. For example, look up "partition" in wikipedia and you can get some education. Try various partition strategies.  Do a few installs.

Then You can learn about boot loaders. See, for example, if you can find the "illustrated grub site," which shows the kind of dedication that open-source inspires.

---

### Post by shaydee on 2007-08-16
> 
I still didn't understand the way Ubuntu Linux file system works and about formatting(See the 1st questions)

You will certainly be able to install Ubuntu on your so called "G:" partition, if you have the Ubuntu installer format it for you. However, the installer will not call this partition "G:". My guess is that it'll call it "hda5", but don't rely on that. The best way to recognize a partition is its exact size, and the physical disk it belongs to. 
The good news is that Ubuntu will allow you to access all the other partitions. However, you won't be able to get write access to them easily if they are NTFS. FAT32, on the other hand, is also writable from within Ubuntu, but I guess that you won't be able to change the filesystem of the partitions in question now. At least you have the option to back up the data.
Anyways, Linux has its own way of labeling devices/partitions/mounted drives. If you are keen on understanding of how all that works, then it is imperative to realize that all three options exist on different layers. 
First of all, your physical harddisks will appear as hdx (whilst x is a letter from "a" through "z") in the /dev folder. But luckily you won't have to worry about these for a long time, unless you want to dig deeper into the system (I.e. forget it for now). The second point is that all partitions will also appear as "files" in the /dev folder (lets call it "directory" from now on). In most cases, this is also not of your concern just yet. The third, and important thing is, that Ubuntu will automatically "mount" your existing partitions in the /media directory. That means... if you want to access your "old" partitions, just take a look into the /media directory. You might have noticed that I have not yet said anything about "C:" or "G:", or anything like that. The reason for that is that Linux systems don't treat partitions like Windows does. In Ubuntu a partition is merely a sub- directory/folder of the root partition. That means: If the Windows "G:" is your Ubuntu root directory, then you will most likely be able to access your old files from the Windows partition called "C:" via /media/hda1 (that name is just a wild guess). 
It takes a bit of "getting-used-to-it" before one understands that partitions are no longer drive-letters, but folders.

> 
Which is the best File System for Ubuntu(Now i am talking about ext3 and other File systems)
Ext3 is just fine. There are even (3rd party) Windows drivers available that allow you to access ext3 partitions, in case you get lost totally.
[QUOTE=]
I have 0 experience about programming. As i am willing to use Ubuntu Fully , which programming language should i start with?
[/quote]
This is a really wild question. Personally, I'd say that one can program anything on any operating system, as long as one has the necessary tools and knowledge. Sure, on linux you can power up your favourite text editor and write/compile your first C program in no time.However, this might not be the easiest way to get into the adventure of making a computer do what you want it to do. One of my predecessors suggested you to get into bash scripting, and I'm sure that over time this would lead you to a deeper understanding on how linux/unix systems work. And that's more or less a "must-do". But its certainly not the way to get a quick-success-encounter. 
Once you feel confident with the system you are controlling, then you might want to get into Python programming. Others might suggest Perl or PHP (PHP has a really steep learning courve, but it's got "bad style" - you might want to have a look at it anyways).
> 
3)After few months i Quick Format my C:Partition on which WindowsXP is installed and Clean install Windows. Can i do the same with Ubuntu if yes please tell me the process.

Yes and no. There's a thing called "bootloader" (which has been mentioned by one of my predecessors). This is a little program that starts before any operating system is booting. That way the bootloader is able to (let you) choose which partition/operating system you want to boot from, before the (selected) operating system kicks in and takes over command of your computer. As a rule of thumb: If you install Windows, it will kill all bootloader options and claim full command of your computer. If you install Ubuntu onto a seperate partition, then a bootloader will automatically be installed that will let you choose which operating system to boot, when you start your computer. 
There are a couple of guides and wiki entries on how to restore Ubuntu boot options after a Windows install. However, I found the easiest way to get the "alternate" Ubuntu CD and then select the "restore" (not sure if its got exactly this name, but it'll be something like that) option, which works just like the Windows restore thing, Except it (re-)installs the bootloader properly so that you can choose your operating system of choice upon booting the computer.

Oh, P.S.: You won't need to re-install Ubuntu in order to fix problems. On the one hand this might sound nice, but on the other hand it really means: you'll have to fix the bug in your current system,  because a re-install won't help at all. That might sound gloomy on first sight, but in practice it does lead to a very stable system. Given you have the time that is required to invest, though.

Also, many of my predecessors have mentioned a sperate "/home" partition. And they are right, saying that most of your systems setting will be stored there. There is no such thing as a "registry" in Ubuntu. Everything there is is stored or referenced via the filesystem. For example, lets assume your favourite torrent downloading program in Ubuntu lets you specify where you want the downloaded files to go to. If we were in Windows, there would probably be a path setting in the registry. On Ubuntu, however, everything is stored in plain files. Usually, these configuration files are hidden by default (naming conventions say that each file/directory that begins with a dot (".") is hidden). So all you need to do is edit these "hidden" files in order to dig deeper into your systems configuration. Well, in a nutshell: What I mean is that, if you have your own "/home" partition, then this will always the place where system-related settings will be stored. Imagine splitting your G: drive into two ext3 partitions.... one is the system partition, the other one is your "/home". If you now format/re-install your system partition, then all your config data will still be available via the (second) /home partition.

---

