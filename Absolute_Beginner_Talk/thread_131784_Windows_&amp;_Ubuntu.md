---
title: "Windows &amp; Ubuntu"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by ibh on 2006-02-17
Before installing Ubuntu I want to make absolutly sure of one thing:

I currently have Windows XP Professional (SP2) and all Microsoft Office programs 2003 (except Frontpage) installed. I do not have the CD to re-install them.

When I install Ubuntu will these programs still stay there and will they still work on my computer?

Will everything on my computer change such as the way it starts up, user accounts, desktop, etc. or will I just have additional software.

Will someone please tell me ALL the changes that Ubuntu makes to my system, as I use a shared computer and don't want to mess anything up or lose Windows applications.

---

### Post by Clark Nova on 2006-02-17
If you install Ubunto to another partition or hard drive on your system then, yes, your Windows installation will still be there. Ubuntu will setup the GRUB bootloader on your system and you will be able to choose to load into Windows or Ubuntu when you turn your machine on. 

If Windows is installed on your machine in an unpartitioned hard drive then you will have to use a program like Partition Magic to resize the partition and create a new one, otherwise you will lose Windows as you will be installing Ubuntu over the top of it. I'm not a big fan of Partition Magic, it's earned itself the name "Partition Tragic" for a reason but I find if you only do a single operation at a time ie don't tell it to do lots of things and queue them up you should be ok.:)

---

### Post by ibh on 2006-02-17
I have no idea what an unpartition hard drive is!

---

### Post by darf681 on 2006-02-17
Have you used the Live CD?  It would probably be your best bet, as it will not install anything to the Hard Drive at all to boot up.  I hve not exclusively with it before, but i would think that you could even store your data on the Hard disk, and certainly on floppies.

---

### Post by wcks48 on 2006-02-17
Don't worry. As long as u have 2 different partitions, one is for WINDOWS, and the other is without any OS, u could install the linux into the Nonwindows parition. I think need to rename that partition as root or simply start with the sign "/", then linux will be installed into that drive. as mentioned inside yr first reply, ubuntu will install Gnub into yr system as multi-OS loading. when yr pc switched on, the gnub wil pop out and ask u which OS u want to be... that means can choose either windows or Kubuntu. 

i got no problem running the install, but better u check out all other matters such as devices drivers. becoz my canon printer doesn't comes with the linux driver, so can't print with the Open ofice in linux. so sad...\\:D/

---

### Post by AndyCooll on 2006-02-17
It is likely that if you only have XP on your pc then your hard drive is one big partition. The Ubuntu installer can take you through resizing and creating a new partition for your Ubuntu OS (you shouldn't need to use Partition Magic or anything like that). I know, because I have done it! 

My hard drive was one big 80gb drive which I split into two 40gb partitions. As with all these things it isn't foolproof however I can only report back that I had no problems and all my applications were still working fine after the resize.

There is a thread somewhere here on the forums that links to an excellent website showing you how to go about it. I'll post back when I find it.

:cool:

---

### Post by AndyCooll on 2006-02-17
Here it is:
[Ubuntu Dual Boot]("http://users.bigpond.net.au/hermanzone/")

:cool:

---

### Post by arctic on 2006-02-17
[QUOTE=ibh]I have no idea what an unpartition hard drive is![/QUOTE]A harddrive needs to be "equipped" with a filesystem in order to operate. Windows XP uses the NTFS filesystem and, unless you tell the system otherwise, it will spread this filesystem on the whole harddisk. Thus you will have ONE partition on it and it is considered unpartitioned (not "splitted up") and formatted. If there ain't any filesystem on it, a harddrive is considered unformatted (an unpartitioned), if there ain't any partitions and no filesystem, the drive is in a bare-naked state.

If you plan to add e.g. another operating system like Linux to your computer, you need to free up some space for this OS, as it will use its own fileformat (not the Windows NTFS format, but e.g. ext3). You free up this space by "splitting" or, better said, partitioning your drive with tools like qtparted or partitionmagic. Once you have shrinked your first partitions size, you have some space left for creating the new partition and your harddrive will be able to house at least two partitions now. You can have up to four primary partitions and many, many logical partitions on one harddisk.

---

### Post by tweetybird on 2006-02-17
This is my recomendation, coming from a windows user, who has been trying to make the change to Linux for over 10 years, but has not been able to, due to no version of Linux I have found working nice with all my hardware, ever.

If you don't even know what a partition is, and how to make changes to them, you do not have your windows CD, DO NOT INSTALL LINUX TO YOUR ONLY MACHINE.

You will not have just additional software - Linux is an Operating System, the same as Windows, and uses all it's own software. 

It will change the boot up to give you the option of starting Linux or XP - FROM THAT TIME FORWARD 
(Linux users, yes I know he can change the mbr, but he does not know what the mbr is, nor does he have the XP CD to easily make the change, and which one of you is going to hold his hand to help him make a bootable floppy or CD when he gets tired of playing with it?)

ibh - If you would like to try Linux, download and try the Live CD - it will boot right into Linux, make no changes to your harddrive, and allow you to play with it some.  If you like it and want to proceed further, read some more of the setup and installation instructioins - you can buy a USB key - like a small hard drive - boot into Ubuntu still from the CD, save all your changes to the key to maintain your persoanl settings until you get comfortable enough with Linux to decide you do want it on your machine.

YES - it can mess up your machine trying to install it  (though not likely) - it is possible that the bootloader (the thing that Linux installs to give you the option of starting Linux or windows) will not work properly and you will be back to spending a lot of time reading and on the forums trying to get it fixed to be able to boot up into either one or them.

---

### Post by damianubuntu on 2006-02-17
another possibility which worked for me is to go to a local pc shop (small guy who fixes things, not great big corporation, and ask if they've got any old hard drives that are OK.  I picked up 3 6GB hdds for UKP5!  Put one in as a slave, and installed ubuntu onto it.  No risk to the XP drive at all.  6GB isnt loads, but it was enough to get me up and running on a machine that would maybe have struggled to run the live CD (accordin to some reports (celeron 500, 256 mb ram))

**I also read that if you are going to repartition the drive, make sure you defrag first.**

Good luck
D.

---

### Post by mr_mop on 2006-02-17
Yes, if its a shared PC, use a LiveCD.
As has been said, if you want to experiment with Linux, get an old junky PC and install on that.
If you install Ubuntu as a dual boot, it is possible to erase everything by mistake, so be warned! :)

The other way to do it would be to buy a 2nd hard drive.  Put that in the PC case.
When it comes to installing Ubuntu, only install on the 2nd drive.  When it asks about GRUB install that on a floppy disk.
That way the Windows drive remains separate from the linux drive and the only way to boot linux would be with the floppy.
It wouldn't do anything to the windows drive at all then.

---

### Post by fredtal on 2006-02-17
I agree with Tweetybird.  A live CD is a great way to learn Linux and they come in handy when Windows won't work and you need some files.  Next get a cheap box (even a $500 laptop will work) and install Linux exclusivily.  This will allow you to learn about networking the two operating systems.  And you will have no chance of corrupting your windows box.

---

### Post by Netisan on 2006-02-17
You just need to ensure not to choose the first option when installing on windows HDD. Create a new single (5-6G) partition, and it's enough. If you use a multiuser pc, try customizing the GRUB loader menu to avoid confusion.

The Live CD works poorly. It's not the option.

---

### Post by aysiu on 2006-02-17
[QUOTE=Netisan]
The Live CD works poorly. It's not the option.[/QUOTE] It works just fine for me. Can you explain what worked "poorly" about it for you?

I'll tell you--before I took the "dual boot plunge," I played around with Knoppix for a good week or so, just familiarizing myself with using Linux interfaces (well, the KDE desktop, specifically).

I wouldn't install anything until you feel more comfortable with things.

That said, dual-boot guides don't get much better than Herman's guide (the fifth link of my signature).

---

