---
title: "Newbie Needs Help Please"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by jeremycollins08 on 2008-03-19
I have gotten my new Ubuntu 7.10 CD in the mail! I am a complete noob to linux, and have always been a Windows XP'er. I want to have something better and different than Windows XP or Vista, and Ubuntu seems to be good. I have many questions, but I really need to know a few of the ones listed below:

[LIST=1]
[*]How do I know if all of my software/hardware will work with Ubuntu? I have a Logitech Surround Sound Speaker System, Norton Anti virus, a Lexmark X3430 All In One Printer, a D-Link Wireless Antennae for wireless internet from a router, DVD Burner with Roxio Software, Webroot Spy Sweeper, and Quicktime with iTunes for my iPod.
[*]What is an oog file? Are there not mp3, avi, etc in ubuntu/Linux?
[*]Is it possible to install Ubuntu, and still keep windows, in case of a crash, and I may need to reinstall Windows?
[*]I saw a video with a cube effect, and motion backgrounds on Ubuntu. Can I get these for my version?
[*]How can I tell if a certain software will work on Ubuntu? Will all Linux software work?
[*]Are iPods and other mp3 players compatible with ubuntu?
[/LIST]

I hope this is not too much to ask for. I really like the interface, but couldn't get my internet to work from the live cd. I have a d-link wireless antennae, which plugs in via USB. The D-Link software says it's compatible with Linux. Any help here is greatly appreciated!

---

### Post by Zubatron on 2008-03-19
I can anwser some of those questions:

1. You don't need an anti virus for Linux especially Norton (talk about death to an OS). You're wireless should work and as with the surround sound speaker system. Not sure about the printer I'm horrible with them.

3. Yes you can still keep Windows. When installing Linux you can partitiion part of your hard drive to where it will only run Ubuntu on that.

6. Ipods can be compatible with Linux, you can install Wine and then install Itunes and viola! Itunes works.

Hope that helped some

---

### Post by Sef on 2008-03-19
1) > How do I know if all of my software/hardware will work with Ubuntu? I have a Logitech Surround Sound Speaker System, Norton Anti virus, a Lexmark X3430 All In One Printer, a D-Link Wireless Antennae for wireless internet from a router, DVD Burner with Roxio Software, Webroot Spy Sweeper, and Quicktime with iTunes for my iPod.

Run the Live CD and see what works.  For some things you may need to download codecs. OpenPrinting says that the [X3450 is paperweight]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-X3450"), so yours would be highly unlikely to work with GNU/Linux.   Lexmark keeps the drivers proprietary.   OpenPrinting says the [best printers are HP and Epson]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters").   For your DVD, there is other software, but Roxio may have GNU/Linux drivers.  No need for anti-virus or spyware sweepers as malware like that does not exist for GNU/Linux.   There are quicktime, pm3, avi codecs.  

2) > What is an oog file? Are there not mp3, avi, etc in ubuntu/Linux?

[oog]("http://www.vorbis.com") is an open format for audio.   You can download codecs for mp3, avi, etc.   You can also check its [Wiki]("http://en.wikipedia.org/wiki/Ogg").

3) > # Is it possible to install Ubuntu, and still keep windows, in case of a crash, and I may need to reinstall Windows?

Yes, you can dual boot.  Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

4) > I saw a video with a cube effect, and motion backgrounds on Ubuntu. Can I get these for my version?

Depends on your system specs including your motherboard, ram, graphics card.

5) > How can I tell if a certain software will work on Ubuntu? Will all Linux software work?

If it is from Ubuntu's respositories, it almost certainly will work.  Ubuntu uses .deb instead of .exe, .rpm, etc.

6) > Are iPods and other mp3 players compatible with ubuntu? 

Yes, most are compatible, but check with others on this forum as to what works OOTB (Out of the Box) or if tweaking is needed, or if they are paperweights.

---

### Post by NightwishFan on 2008-03-19
1. Software is a no. Hardware is usually good, except for printers and wireless which more or less work.
2. Ogg is an open source container format for vorbis and theora. Yes there is mp3 and such in linux.
3. With supported hardware you will never need to scurry back to windows like its a safety net. I wouldn't want windows anywhere near my hardware. (yes you can dual boot)
4. Motion backgrounds I have heard of not sure how. Cube is by default on supported hardware. Just install the compiz control panel to configure it. What is the hype with the cube anyway, water effects are cooler.
5. There are over 20,000 applications one click installable from the repos.
6. Yes most mp3 players worked for me. Create new threads if you encounter problems.

Are you really ready to take the plunge? Perhaps keep with the live CD until you are ready. (Note the installed system is faster by a factor of 10 than the live CD)

---

### Post by jeremycollins08 on 2008-03-19
Thanks for all the replies! As you can tell, I am a windows user, and need a change. A tech supervisor at the local school informed me of Ubuntu, and I checked it out. He got me a cd, and so I wanted to give it a go. It will be hard to switch if my printer will not work. Just bought a new one at that!

In the Live CD, the extra graphic effects worked fine, so I assume that means it will work on the installed version. 

Also, what are these water effects you speak of NightwishFan?

I think I will give it a go, and see how everything turns out. I just fear I may have a computer crash (although my computer is only 1 1/2 years old, it does crash). What is the average installation time for Ubuntu also?

Thanks for your help, and I was blown away by the quick responses!

---

### Post by NightwishFan on 2008-03-19
=D
Windows crashes. Your computer will likely be fine.

The water effects are a part of compiz as well, they are like ripples on your screen.

Dual boot to use printer if it does not work. It might.

---

### Post by jeremycollins08 on 2008-03-20
Ok. I absolutely could not get my wireless antennae to work on the live cd. No internet at all. Will I need to install the cd software for D-Link on Ubuntu? It says it's linux, windows, and mac compatible.

---

### Post by NightwishFan on 2008-03-20
Once you get installed you can install software so I suppose that will work. I do not know anyone with wireless so that is a gray area with me.

---

### Post by amd-64 on 2008-03-20
jeremycollins08 

Wireless will most likely work. It may require some tweaking.

To start working on wireless, post the specs of your wireless antenna. If you dont know what it is, while the live CD is running, you can open a terminal or a command window, 

type the following 
lspci

Look for one line in the output with the wireless specs, on my laptop it is 
 
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

Write down the information and post to this thread.

---

### Post by jeremycollins08 on 2008-03-20
Ok, thanks!

I will log off and run the live cd and post the results in a few minutes.

---

### Post by jeremycollins08 on 2008-03-20
Ok. I ran the command 

lspci

in the Terminal on the live cd. It came up with a long line of text, which I couldn't copy/past/print. I wrote down anything that looked to be wireless related. BTW, I am using a wireless usb adapton from D-Link, that is not a wireless card, but plugs in via USB, and picks up a signal. So, I wrote down the ones that said USB on it. Here they are:

00:1d.0 USB Controller: Intel Corporations 82801EB/ER (ICH5/ICH5R) USB Controller #1 


00:1d.1 USB Controller: Intel Corporations 82801EB/ER (ICH5/ICH5R) USB Controller #2


00:1d.3 USB Controller: Intel Corporations 82801EB/ER (ICH5/ICH5R) USB Controller #3


00:1d.0 USB Controller: Intel Corporations 82801EB/ER (ICH5/ICH5R) USB Controller #4


01:01.0 Modem: Intel Corporations FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)


01:08:00 Ethernet Controller Intel Corporations 82562EZ 10/100 Ethernet Controller (rev 02)


I am not sure if that is what you needed or not.

I did a product search on my dlink adapter, and its not an antennae, I thought it was, but was mistaken. Here is the product page to clear that up 

[http://www.dlink.com/products/?pid=652](http://www.dlink.com/products/?pid=652).


Thanks!!!

---

### Post by Andavane on 2008-03-20
> **jeremycollins08 said:**
>  It will be hard to switch if my printer will not work. Just bought a new one at that!
If you've just bought a new printer, it will almost certainly work with Ubuntu.
Set it to dual boot and see.
If you get problems someone here will help you.
Regards
John

---

### Post by jeremycollins08 on 2008-03-20
Ok. The printer is not new as in just bought it today. It's about a month old or so. But that's still new to me!

I will set it to dual mode, and see, but I will have to do so tomorrow. I'm going to have to log off, and I'll be back tomorrow afternoon. Any replies will still be greatly apprechiated, and I'll respond tomorrow throught the day if possible. 

Thanks!

---

### Post by amd-64 on 2008-03-20
The usb adapter will work, there is a driver and some instructions. Try this link and see.  [http://ubuntuforums.org/showthread.php?t=475847](http://ubuntuforums.org/showthread.php?t=475847)

I recommend you try this on a real install not on a liveCD. You could install linux in a new partition, without removing windows at all. If you have an unused partition in your hard drive. 

Linux can be removed later if you figure you don't want to keep it. This process is 100% reversible as long as you install in 5-10 Gb new partition. Linux does not leave a mess behind.

---

### Post by jeremycollins08 on 2008-03-20
Ok...so I am going to do a Dual Boot. One question though...if I do do a dual boot, and fall in love with linux, then could I reinstall Ubuntu and use my whole hard drive for it, instead of part Ubuntu and part Windows... basically starting over?

Also...how do you know which of these (NTFS or FAT) you have?

---

### Post by NightwishFan on 2008-03-20
In a terminal type:
```
sudo fdisk -l
```
That will tell you what is on your hard drive.

You could also boot the live cd for ubuntu, and delete the Windows partitions and resize the Ubuntu ext3 one. Using gparted of course. It is in the system menu somewhere, called partition editor.

---

### Post by munch3 on 2008-03-20
1.You don't.The biggest problem in Ubuntu is hardware support.But U can always check for drivers via Google.I can tell U that wireless net should automatically work and eventhought there are plenty apps for linux which are alternatives to the ones on Windows, if u want the same one, you can install an app called Wine which will run windows apps on Linux.
2.Yes, you can dload codecs an play every media file that u can play on windows.
3.Yes, if u install linux on a different partition than winodws, a thing called GRUB will auto set up a dual-boot system, so when U start up ur PC u'll be able o choose between Windows and Linux.
4.Yes ofcourse, this is called Compiz Fusion (to install search for compiz in add/remove programs) or Beryl if u have a version older than 7.10.
5.If your hardware supports it yes.Most of windows apps will work with wine.
6.Sure, you can find apps that r used for iPod users.

Don't forget to create a SWAP partition of 1gb or so when installing :)

---

### Post by jeremycollins08 on 2008-03-20
Ok. So I want to give my perspective of what I need to do. Please correct me if I am wrong =)

[LIST=1]
[*]Install Ubuntu and Windows XP by the Manual Partition Choice in the Ubuntu Install
[*]Create a swap of 1gb
[*]Make a new partition for Ubuntu to use, with space at least 2gb
[*]Change the Use as: to ext3
[*]Right click on the partition ext3 and click edit
[*]Change the mount point to a /
[*]Check the box to format etx3
[*]Then Intall
[*]Install Updates
[*]Install the d-link cd (says it supports linux)? not sure on this one yet
[*]If I ever want to wipe away Windows, and use my whole hard drive for Ubuntu, use the partition editor and delete the partition for Windows
[/LIST]

How does that sound? I am going off of a guide I found on Google "http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty"

---

### Post by NightwishFan on 2008-03-20
If you have a space already partitioned use the "use largest continuous free space" option. That will set up on the empty partition and create a swap on its own.

---

### Post by Sef on 2008-03-20
> Dual boot to use printer if it does not work. It might.

Another option would be to set up a Windows box as a print server.

---

### Post by jeremycollins08 on 2008-03-20
> **NightwishFan said:**
> If you have a space already partitioned use the "use largest continuous free space" option. That will set up on the empty partition and create a swap on its own.

I don't know if I do. A computer tech guy installed everything again, once Windows crashed about a year ago, so I really don't know how he did it.

---

### Post by NightwishFan on 2008-03-20
You likely do not then. I suppose you can do option to auto resize too. Well you can post during the install, so no problem.

---

### Post by jeremycollins08 on 2008-03-20
Could I do what this person did? [http://youtube.com/watch?v=JBfl3oViny8](http://youtube.com/watch?v=JBfl3oViny8)

I assume that modifying the partition for Windows on the live cd is safe? Also, will doing that destroy anything in Windows?

---

### Post by NightwishFan on 2008-03-20
i do not have flash installed bear with me. Resizing the partition should not cause any problems as long as you have a lot of space free. It gives a slider to show you how much space you want in the new partition and how much you want to leave in the old one.

---

### Post by jeremycollins08 on 2008-03-20
Ok, I know I have like 60 or 70 GB of free space, out of an 80GB hard drive. I back up files and deleted them off of windows into a storage drive, thats why I have a lot of free space.

---

### Post by NightwishFan on 2008-03-20
Well tell me when you get to the partitioning part of the install and I will help you.

---

### Post by jeremycollins08 on 2008-03-20
Ok. Should I modify any partitions in the live cd for Dual Boot or anything, or leave everything alone and begin install?

---

### Post by jeremycollins08 on 2008-03-20
Oh, I just found out I have NTSF. I looked in the defrag and it said that.

---

### Post by jeremycollins08 on 2008-03-20
On the install...my location (or anywhere near me) is not listed :(

I live in Trumann, Arkansas (near Memphis TN, but thats not listed either)???

---

### Post by cedavis8 on 2008-03-20
> **Zubatron said:**
> 
6. Ipods can be compatible with Linux, you can install Wine and then install Itunes and viola! Itunes works.


iTunes does not work, even with Wine...just so you know. You have to get an open source thing that can connect to your iPod...

---

### Post by jeremycollins08 on 2008-03-20
> **cedavis8 said:**
> iTunes does not work, even with Wine...just so you know. You have to get an open source thing that can connect to your iPod...

As long as it works...I am not a huge fan of itunes anyway.

Also...do I really need to defrag my windows comp 3-4 times as said in a tutorial for dual boot?
Is it a good idea to have the partitioner automatically set the partitions for Ubuntu and resize the windows partition?

In the partition manager in Ubuntu live cd, there are two boxes, one with windows and another that is called "Recover". What is this "Recover" partition?

I am aiming for the cleanest and the best install as possible, but I am no expert at all on this stuff. I am new to Linux!

---

### Post by NightwishFan on 2008-03-20
Well. I think running a defrag once is good. I was able to use the partitioner to get 116gb of space for Ubuntu and around 70 for windows before I deleted it.

---

