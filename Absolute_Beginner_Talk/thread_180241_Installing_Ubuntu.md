---
title: "Installing Ubuntu"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Ched on 2006-05-21
Hey guys, im pretty new to Ubuntu and I have a few questions about installing it. I have a live CD and an install CD (I dont know if this makes any difference). My problem is installing it as another partition. My biggest fear is installing it over Windows XP, losing pretty much everything on my computer. Is there a way when it boot, I can choose which OS to boot from? I have absolutely no experance installing OSs, and i dont want to do something stupid and mess up my hard drive. 

Thanks in advance for any of your help. :)

---

### Post by aysiu on 2006-05-21
Be 100% sure you lose nothing:
1. Back up your data
2. [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Be 99.9% sure you lose nothing:
1. Don't back up your data
2. [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by aktiwers on 2006-05-21
Hi and welcome!

Im new too, but I have learned that Ubuntu boots from a program that is called Grub. If Windows XP is installed, you can choose dual-boot with it. So when you turn on your machine, you can pick wich one to boot from.

Ubuntu  or Windows.

But! When I installed Ubuntu, something damaged my windows bootloader (or something like that), so I lost my installation. 

So remember to back up importent stuff!!
You could create a patition for this.

Sorry I cant be more helpfull..  hope I atleast answered your duelboot problem a little.

But lets wait and see if someone else replys.

---

### Post by Ched on 2006-05-21
Thanks!

---

### Post by wpshooter on 2006-05-21
Ched:

My advice would be to, if at all possible, experiment with Ubuntu on another computer that has an Windows type operating system that it doesn't makes any difference if you lose.  

That way you can get sort of a feel for the way the partitioning and formatting of the Ubuntu O/S is going to work.  But ultimately, the goal is going to be to get rid of Windows all together.  So, experiment with Ubuntu/linux with that goal in mind but having Windows as a fall back system for now until all the kinks are worked out of Ubuntu.  

And let me warn you that Ubuntu and Linux in general is NOT windows, so don't get discourged right off the bat, give it a fair chance, in remembering that Linux is still in many ways tied to the prompt/command line/terminal mind set, i.e. there is a lot of stuff that is not just a point and click away.  But I have not double that this will change with time.  There are just to many average computer users that will just not be able to perform these task in a command line type of enviroment.  Heck, many of them can't do the fairly simple needed chores in a strictly modern Windows environment.

Good luck.

---

### Post by aysiu on 2006-05-21
Taking wpshooter's suggestion a bit further--use the live CD for two weeks before you install Ubuntu.

---

### Post by sailor2001 on 2006-05-21
a caution.. defrag  defrag defrag before atempting to install linux as a dual boot

---

### Post by catlett on 2006-05-21
The install is very safe but you should always have a backup. People with only one system should be backing up their system regularly. Things can happen.
That aside the installers are safe. I have 2 computers. One has Xp and 3 linux distros and the other has XP and 5 linux distros on it. All side by side in different partitions and each one is bootable from a single menu.
I say this only to give you a little confidence in linux. Practically every weekend  I install another distro. Erasing one I dislike and installing another to that partition. There are literally hundreds of distros out there.
There is a difference betwen a live cd and an install cd. The live cd doesn't touch your hard drive. It runs off the cd. Put it in and restart your computer. Ubuntu will run fron the cd. This way you can get a feel of ubuntu. Most importantly you can see how well ubuntu detects your hardware.
If the live cd starts right up and you have video, sound and an internet connection, go forward with the install cd.
Put that in and start your computer. Press enter to get the install started. Eventually, after a few dialogue pages, you will get to the partitioner. There is an easy and simple option to use. It will resize your disk. The option says something like "resize your drive and install ". What happens is the installer will shrink your XP partiton and then automatically create partitions for your Ubuntu sytem. After that follow the prompts. 
When it gets to the end it will install the bootloader. You have to install this boot loader if you want to have a choice of Windows and Ubuntu. The windows loader will not recognise Ubuntu. The program is very stable and used by almost all distros. If you don't think so just look at its name GRUB (grand unified bootloader):D 
It will overwrite the MBR and the windows loader will be gone but Grub can boot you into windows. The MBR will be gone but your system won't. If you ever have an issue and something happens you can always rewrite the bootloader from an XP install or rescue disk. Boot to recovery mode and enter "fixmbr" (without quotes). This will overwrite grub and put windows' loader back.
Follow the guides in Aysiu post. They are very thorough and you can see a screen shot of the "resize" option I mentioned. Good luck and post if you have more questions.

---

### Post by Ched on 2006-05-22
Thanks for everything guys, you pretty much hit the nail on the head. :)

---

