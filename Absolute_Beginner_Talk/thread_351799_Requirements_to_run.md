---
title: "Requirements to run"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Xolo on 2007-02-02
Hi all,

I'm new to the Ubutu OS and I need some info before proceeding this weekend to install it onto my oldest PC.

First off, what format does the HD need to run it? I've got my HD's formatted as NTFS....do I need to re-format and if so is that option already on the CD?

Are there any suggestions as to HD format set-ups for optimal running of the OS? Typically with MS I use a 5Gig partition for the OS, a 5Gig partition for temporary files, a 10-15Gig partition for programs and then the rest for storage.....is something like this recommended for running Ubutu?

I'm running a dual monitor set-up and tried running it first from the CD. Only one monitor displayed correctly. Should there be better drivers once I install the full OS or should I expect to see the same kind of display problem (I hope not as I have 4 PC's with dual monitor displays and I am going to get used to navigating through the new OS before converting all of them to Ubutu)?

I've read some posts and found out that several people have had problems with their wireless cards and routers. Should I expect the same kind of problems? I have the network set up (by an expert that I bring in) but should it be much of a problem to add this PC back onto the system?

Do RAID set-ups work the same with this OS as with Windoze?

Is there a way to run any of my MS software on Ubutu? I have several programs that I am going to want to test to see how they run. Mainly, I will need to test out AutoCAD in an Ubutu enviroment to make sure that it's as functional with this OS. Otherwise I can't convert all of my PC's over as I need that for business.

I've printed off the user manual, and will be reading through it over the next couple of days, but I will need more input to get the most out of this OS and to be able to run it the way that I want it.

Thanks to all in advance for all of your help here.

Cheers!

Xolo

---

### Post by shareMenaPeace on 2007-02-02
Hi,
for install on older machines use teh alternate cd iso or try xubuntu which is specialy designed for low performance systems and most application works there too liek openOffice.

---

### Post by irish_flu on 2007-02-02
Hello friend,

Linux does not use NTFS, it has its own file system.  If I read you correctly, this PC won't have Windows installed alongside Linux, is that correct?

Assuming this is a Linux-only machine (and assume there's nothing you want on that hard drive) when you pop the Ubuntu CD in and begin installing, you'll get the answers to a few of your questions.  There's a partitioning tool included (and that will be presented to you by default) that will:
-format the hard disk correctly
- partition the hard disk optimally

Most of  your other questions are things I have no experience with, so I'll leave them to others.  However, as far as Windows applications are concerned, you should check into an application (which is easy to get from the Ubuntu "repositories") called WINE.

WINE helps you run many Windows applications in Linux.  It's far from perfect, though, and there are also many applications it won't help you run.  I think AutoCad is common enough that if you Google around a bit, you'll find an answer as to whether or not it will run in WINE.

---

### Post by steve.horsley on 2007-02-02
> **Xolo said:**
> Hi all,

I'm new to the Ubutu OS and I need some info before proceeding this weekend to install it onto my oldest PC.

First off, what format does the HD need to run it? I've got my HD's formatted as NTFS....do I need to re-format and if so is that option already on the CD?

Are there any suggestions as to HD format set-ups for optimal running of the OS? Typically with MS I use a 5Gig partition for the OS, a 5Gig partition for temporary files, a 10-15Gig partition for programs and then the rest for storage.....is something like this recommended for running Ubutu?

Ubuntu (all Linuxes) use their own partition types. The Ubuntu installer by default installs one large ext3 format partition for the data etc, and one smallish swap partition (functions like the swap file in Windows). 

When you run the installer, you get 3 options.
1) Erase and re-use the entire disk
2) Resize the windows partition and use the regained space
3) custom partitioning (define your own scheme)

If you intend to shrink the NTFS partition, make sure you deftrag it thoroughly first. 

With custom partitioning, you may want to have separate root (/) and /home partitions - all user data is stored in /home, so this allows reinstallation without trashing the user data. You might even allocate a spare partition for another system like I do, so I can test the next version.

For the system you need at least 3G, and up to 10G if you install lots of stuff.
Swap shoud be 1-2G. Options 1 and 2 auto-size the swap and allocate one partition for the rest.
> 
I'm running a dual monitor set-up and tried running it first from the CD. Only one monitor displayed correctly. Should there be better drivers once I install the full OS or should I expect to see the same kind of display problem (I hope not as I have 4 PC's with dual monitor displays and I am going to get used to navigating through the new OS before converting all of them to Ubutu)?

You can install custom drivers for nVidia and ATI after the base inatall. This will give 3d acceleration and maybe a utility for extra configuration. nVidia seems good in this respect. ATI tend to be problematic.
> 
I've read some posts and found out that several people have had problems with their wireless cards and routers. Should I expect the same kind of problems? I have the network set up (by an expert that I bring in) but should it be much of a problem to add this PC back onto the system?

Expect problems. The driver situation for wireless is dire at the moment, with all the well supported chipsets having been discontinued.
> 
Do RAID set-ups work the same with this OS as with Windoze?

Sorry, don't know. There is Logical Volume Manager which makes logical volumes spam many physical ones, but I don't know if it includes raid.
> 
Is there a way to run any of my MS software on Ubutu? I have several programs that I am going to want to test to see how they run. Mainly, I will need to test out AutoCAD in an Ubutu enviroment to make sure that it's as functional with this OS. Otherwise I can't convert all of my PC's over as I need that for business.

Some stuff runs in wine, or you may need something like vmware. Try it and see, or look at the wine compatibility tables (winehq.org).
> 
I've printed off the user manual, and will be reading through it over the next couple of days, but I will need more input to get the most out of this OS and to be able to run it the way that I want it.

Thanks to all in advance for all of your help here.

Cheers!

Xolo

There's nothing quite like trying it for real. Give it a go. Take backups first. Good luck. Ask here for help if you need it.

---

### Post by glabouni on 2007-02-02
1. to get the best out of ubuntu you should use etx3 as filesystem.
[gparted]("http://gparted.sourceforge.net/") is included on the cd and will run during installation process

2. about partitioning you can read this guide: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) you'll need 3 partitions, for the system itself / or root , for /home partition, and  for swap partition. more about the linux filesystem hierarchy here: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

3. dual monitor is possible with ubuntu. check these for more info on how to achieve it:
[http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)
[http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86](http://wiki.linuxquestions.org/wiki/Using_multiple_monitors_with_XFree86)

4. wireless can be a problem, mostly because hardware manufacturer do not provide linux drivers. some wireless hardware will be working right away, some will need you to spend time to get them working and some witll simply not work.YMMV.

5. I think raid is supported under ubuntu though I know very little in this matter as I don't have a radi array at home.

6. to run windows software under linux there a wonderful thing called [wine]("http://www.winehq.com/") (not all software will work though). another option is to run windows inside a virtual machine. check these guides:
[http://doc.gwos.org/index.php/VMWare_WindowsXP](http://doc.gwos.org/index.php/VMWare_WindowsXP)
[http://doc.gwos.org/index.php/Win2k_xp_vmware_player](http://doc.gwos.org/index.php/Win2k_xp_vmware_player)

welcome aboard !
don't forget that ubuntu comes with gnome, kubuntu with kde and xubuntu with xfce, one of these might suit you more than the others.

---

