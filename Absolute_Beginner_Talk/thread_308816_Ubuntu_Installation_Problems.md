---
title: "Ubuntu Installation Problems"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by KatanaSwordfish on 2006-11-28
Hi, Im a first time poster and also a soon-to-be first time linux user.

Here's the deal. I've been a windows user for my whole life and never really got around to venturing out and trying linux until recently; when my XP had yet another error that stopped me from using my computer at all. I wont go into details on my windows problem, just let you know that it wont boot up regularly or in safe-mode or anything. It just shows the XP splash screen and goes blank and stays that way. Well, i'm an avid gamer and although i've heard good things about linux and am very attracted to the idea of open-source software and a free OS, i never had the drive or motivation to go out and try linux. Possibly just because i may have to relearn a whole new OS, and out of fear of not being able to use all my beloved windows apps. (this was before i knew about wine/cedega and all that good stuff).

So basically im fed up with windows and want to install ubuntu. I made the Ubuntu and Kubuntu bootable CDs and tried them both out and i think im going to go with Ubuntu (edgy; yes i know its not recommended for n00bs but it seems to run fine for me so far.).

My PC setup has 2 HardDrives, and windows is installed on my master drive. For the time being I would like to install ubuntu on my slave drive, which has some files on it now but nothing too important (formatting that drive is an option for me, although i would like to possible just take the files from that drive first and move them to my master drive). Heres part of my problem. My windows will not boot up, and i cant find my windows XP disk, so i have practically no way to move those files that i know of. (my PC is a few years old now, and i just moved recently and my XP installation CD is nowhere to be found, so i cant just run a fix install or anything like that. :( )

The other part of my problem is that IF i decide to format my slave drive completely and install ubuntu on it, will it be possible for me to be able to make it my primary OS for the time being untill i can get ahold of another XP disk. I was looking online and it seems like if i want to dual-boot XP/linux, i need to put some program on my master drive and mess around with some settings in XP.

Working with XP is very frustrating, especially considering i legally bought it and now that i need to fix it, i may have to buy it again! And now that i have tried ubuntu, i dont see any reason to want to use XP in my opinion, aside from lazyness (not wanting to reinstall all my apps/games), and a few choice applications that dont work with wine.

Anyway, thank you very much for the help, any advice or insight on my issue would be very helpful to me. I may not have explained it as clearly as i could have, so just ask away if you need clarification on anything.

Thanks, KAT.

---

### Post by bernied on 2006-11-28
Hi there and welcome to the forums, and also to the worlds of linux and ubuntu.

A few things that might help you.

If you want to save some files from either disk, try using a linux live-cd. These are real linux distributions that run off a cd, so you don't have to install anything to the hard drive. You do need access to a cd-burner, and you do need to be able to boot to a cd (you may need to change a setting in bios, that's the bit of guff that flashes up just before your windows logo comes up). My favorite live-cd is called slax (google it), but there are many others. Check the file-size before you start downloading. When you start up a live-cd, generally it will find your hard-drives and make them accessible for you, if things go really well you may get a network connection straight away as well. They are a fun way to look about linux, but don't run as fast as a full install, because they have to access the cd all the time.

Places you could save the data:
- on your windows disk - this might be difficult (or not) if the disk is formatted in a windows proprietary format called ntfs, if the format is fat16 or fat32, then it is easy
- on your second disk. You can use various utilities (fdisk, cfdisk, parted, gparted) to change the number and/or size of partitions on the disk. So you could make a partition just to keep your saved stuff in, and install ubuntu in a different one.
- on a usb stick or external drive
- on the internet - like email them to yourself

Your legitimate ownership of your windows operating system is dependent on possession of the software key, not the cd itself. If you needed to reinstall windows you could use someone else's CD and your own key and not have any problems with registering it. The key is a crazy string of about 30 numbers and letters that might be on a label attached to the PC, or with the PC documentation, or if you're unlucky, with the cd that you have lost.

and, remember, search engines are your best friend. You just need to know the words to search for.

---

### Post by PotOfVB on 2006-11-28
1.   What happens when you boot from the kubuntu CD?
2.   Is this a live CD or Desktop CD
3.   How far have you got, need more info...

look at this guide it might point you in the right direction:
[http://home.online.no/~osmoma/]("http://home.online.no/~osmoma/")

Kubuntu should automatically set itself to boot at startup (using grub bootloader)

If the data on your second drive has been defragged recently you may be able to partition the drive and save your data

can you boot to windows safe-mode? 
press F8 after memory test and disk drives are shown, when computer is booting up, 
it may bring up a text menu
use arrow keys to select safe-mode, 
press enter

if this doesn't work - are any errors coming up?

---

### Post by turbojugend_gr on 2006-11-28
HI kat, here's my piece of advice, use the ubuntu LiveCD to see if all your hardware is detected (btw can you post your specs, CPU,GPU,router or modem is the ones that matter, all others are unlike to cause you any trouble).

If you find out ubuntu handles your hardware fine, then imo there are many wonderful apps to replace your windoz beloved ones. Just name some apps you like and users here will give alternatives (most useally equal or better) that are Linux native. Linux is nowdays extremely easy for a newcomer, actually it's a lot easier than windows to a person that never touched a PC again. You will just need to learn your way around, since you are used to windows, but that shouldn't be at all difficult. There are some great guides which will answer most of your questions (on how to use your ubuntu) quickly and easily. Your main concern should be the hardware (it's not that Linux is rarely detecting your hardware, it's just that it is the only thing you 'll need to strive to get working if something is not ok). There are many great apps that will get your system firing here, and usually they are just as easy to learn 'em.

---

### Post by goatflyer on 2006-11-28
This will help.

[http://www.oreillynet.com/cs/user/view/cs_msg/86709](http://www.oreillynet.com/cs/user/view/cs_msg/86709)

In your case, you either want to first get the data copied off the second hard drive so you can devote the full drive to Ubuntu, OR during the install you want to shrink the existing NTFS (windows) partition to a smaller amount which still contains those files, and install Linux on the remaining space which has just been freed up.

Both alternatives are possible to do, you have to decide.  If you still have hopes of fixing your existing XP, I would keep a 'second windows drive' alive, if only to reformat it later as FAT32 and use as space for a 'transfer area' for data from Ubuntu to WinXP.

---

### Post by KatanaSwordfish on 2006-11-28
[B]Briefly, hese my PC specs:

- Intel P4 3.2Ghz HT
- Intel motherboard
- nVidia GeForce 6600 vid.card.
- (2) 120GB harddrives.
- Windows XP Home Edition SP2.
[/B]

I have both the UBUNBTU and KUBUNTU live desktop CD's from the ubuntu website. I have been able to run/boot both of them perfectly with my PC.

> If you want to save some files from either disk, try using a linux live-cd. These are real linux distributions that run off a cd, so you don't have to install anything to the hard drive.

Can i use my ubuntu or kubuntu live desktop CD's to do this?

> ...use the ubuntu LiveCD to see if all your hardware is detected...

Both the Ubuntu and Kubuntu desktop disks work perfectly on my computer. I can use them to boot, and all the apps that came with them work fine. The only thing that i am confused about is that when i go to the **Places>Computer** folder, it shows floppy, optical drive, and 'filesystem'. Does it not show my harddrives because their are partitioned under windows (ntfs), and not linux-partitioned?

---

### Post by turbojugend_gr on 2006-11-28
Filesystem in Linux contains all your harddrives, which are mounted in a place under it (for example /winxp is where I decided to mount my winxp partition, /home is where my home partition is and / is my root partition). I know it seems weird, but is shouldn't. A user he doesn't care how many partitions he has, he only cares to be able to locate his files, and this works bigtime, I want my winxp, I decide whre it is and how it should be named, and voila! It is important for other reasons too, but analyzing 'em will take us out of topic.

I would suggest using th ubuntu  not kubuntu since you are a first timer, and it has better doumnentation support since most users use it, thus you will be ableto seek help easier, after all you can install kubuntu with 2/3 clicks anytime using you ubuntu desktop, so if you wish trying it ,you can install it and choose which one you like using then.

No you can't use a LiveCD to write to ntfs, try a usb stick or partioning that drive, or an online storage, all this you can do, ntfs write access is not at all an easy task using your LiveCD.

EDIT: Linux is all about choice, so if you wish your drives to appear, in your computer window (or even your desktop ala macos) that is only one click away, though their mount locations will still exist, you will be able to see them and open them like in windows.

---

### Post by KatanaSwordfish on 2006-11-28
> Filesystem in Linux contains all your harddrives...

OK, but is there something i need to do in ubuntu or windows to make my windows drives show up in my Filesystem?

When i open the filesystem there are many various folders in there, however none appear to be accessing either of my harddrives. Or is it setup so that i can not view files that are in windows formats?

Maybe i am overlooking something. I have a 1GB USB flash drive that i can use to take important files off my slave drive, however, im not sure how to access my slavedrive using my ubuntu live-cd. In windows it is my (: D) drive, is it called something else in linux/ubuntu or is there a certain folder that i should be looking in?

---

### Post by KatanaSwordfish on 2006-11-29
> so if you wish your drives to appear, in your computer window (or even your desktop ala macos) that is only one click away, though their mount locations will still exist, you will be able to see them and open them like in windows.

Please excuse the double post, but, does this mean that I have to do something in order to make my drives show up in my Computer folder? I'm just really not sure where to look to access my slave drive at all. :(

---

### Post by turbojugend_gr on 2006-11-29
Your disks, are not mounted by default in a LiveCD environment, cause if they were you wouldn't be able to format and partition athem (which most ropably will need to do, in order to install). 

You can open a terminal (application>>accessories>>terminal) and there issue the following commands. **"sudo mkdir /winxp"** and then **"sudo mount -t ntfs /dev/hdb1 /winxp"**. This will mount your second drive (if it is ntfs, if it is fat32 change the second command appropriately) which if I remember right you wish to back up to your USB stick, you can access that drive by navigating into /winxp (since that's where we decided to mount it).


P.S: After installation all your drives will be mounted automaticlly, no commands, this is just to bypass the fact the drives where not mounted by default cause we needed to be able to partition 'em.

P.S.1: MAke sure after backupping your data, to restart your pc, and reboot into ubuntu LiveCD, so the drives are unmounted again, and you make sure everything is fine, You can unmount with an easy command (sudo umnount /winxp), but it is safer to restart, plz do so then go on with the installation.

---

