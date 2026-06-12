---
title: "I'M AN ABSOLUTE BEGINNER: needs help!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by lamchopz on 2007-07-06
HI,

I'm planning to rebuild my system from scratch and I would like dual boot Windows XP Professional (default) with Ubuntu 7.04 for desktop.

I have two hard drives: one 40GB and one 250GB.

I know how to partition the drives for and install Windows and all, but I've been reading about Ubuntu and I'm just... lost.

Basically, I'm thinking of putting Windows XP in the first 80GB space of the 250GB drive, followed by 40GB for Ubuntu.

The secondary 40GB remains as backups for importants documents and for Windows XP page file.

I have a couple of questions regarding the installation of Ubuntu Feisty:

1) Many sources suggest I should install XP first. Then run Ubuntu installation. Also they further suggest that I mount the NTFS partition. Would you advise me to do this?

Suppose I would like to read-write data between the two systems. What should I do? Some said I should use NTFS 3g, others went for a separate FAT32 partition.

2) I have troubles finding any documented support for either of my current wireless adapters (I have one Linksys WMP54GR and a Belkin Part # F5D7050).

A suggested solution is to use some Dapper which makes use of the Windows driver for either of the adapters. Err... Am I making any sesne? LOL. Sorry if I confuse you.

3) If I go ahead installing Ubuntu after WIndows, how would I go through the installation process? Is it UI- or command-based? If command-based, where would I find a nice summary which guides me through the whole process?

I will come back with more questions as soon as I can think of them. 

Thanks for any replies.

Cheers,

---

### Post by Smu on 2007-07-06
I'd download the ubuntu live cd and boot from it to test your wireless card. If it works on the live-cd out of the box, then you'll probably won't have any problems with it. If it doesn't work it may need a bit hacking to get it to work... 

It will be much easier to install windows first, that way you get grub installed the right way. I'm not sure on what filesystem you should use, I've read somewhare that FAT would be better with Ext3, but I've had no problems with NTFS. You can install ubuntu directly from the live-cd with a graphical installer.

---

### Post by Rui Pais on 2007-07-06
Install with a GUI (check the pictures :)):
[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)

or command line:
[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

IS up to your preferences ;)

Just to Windows 1st and Ubuntu after.

---

### Post by doomster on 2007-07-06
hello and welcome to ubuntu:) 
first of all  you should install windows xp on your 250gb hard drive, by making your 
NTFS partition (80GB capacity) and leaving the rest of the space unpartitioned. 
After finishing the installation, put Ubuntu festy fawn Live cd on the drive and hit restart.

 You will load Ubuntu from the cd, without harming anything on your windows installation.
after checkinng that everything works correctly(including your wireless cards), hit Install
 from the desktop of Live cd.

Installation of Ubuntu Feisty is In graphical User Interface all the way. 
  Through the install  you should make 1 partition formated in ext3 of 40GB and 1 partition marked 
as Swap  of about 1gb capacity.

  Your windows-ntfs drives/partitions will be readable by default by your ubuntu system ,
and to make them writable you will have to install ntfs-3g program.

i hope i helped clearing things out a bit :)

---

### Post by aquavitae on 2007-07-06
Just a suggestion, but I'd recommend putting the two systems on separate drives.  That way you don't need to worry about your linux installation if you need to reinstall windows.  Its not a huge problem if you don't - just might make life a bit easier late on.

---

### Post by lamchopz on 2007-07-06
Hi, and thank you, everyone

This gotta be the best forum ever. LOL. Four replies within hours of my post.

OK, so I will install Windows first, then Ubuntu (the screenshot sequence of the GUI-based set-up really helps!).

After all the pre-reading, I was about to give up on Ubuntu and just went for a fresh copy of Windows XP. But I really like to try Ubuntu Feisty and enjoy open source for the first time (to be honest, the only open source program I use is Mozilla Thunderbird -  I gave Outlook 2007 a kick after knowing that Microsoft "babysits" users in terms of spam filtering, meaning I can't define my own system of eliminating spams at all).

More questions (I'm so sorry but I have tons of questions before I actually begin working up my system):

1) Aquavitae suggests I should install Linux on the 40GB HDD. His explanation makes sense but the problem is that I planned to keep all critical files and documents, along with Windows XP Page file on this drive. This could mean that there won't be enough space for Ubuntu in the long terms - or for my backups. I insist on using this drive just in case if my Windows drive (250GB) blows up somehow, all of my important data will still sit safely on the 40GB drive. As this is my plan, should I still consider aquavitae's suggestion? I don't have the budget for a third drive (I'm still a student, guys).

2) About the installation:

- (This question is silly but I can't help it): I have a DVD-ROM drive. I read somewhere that Ubuntu doesn't support DVD reading by default. So if I was dumb enough to burn the ISO image of the installer onto a DVD, would the installer still work? OK, please don't laugh. It's only a thought.

- In "Prepare disk space": I truly want my Windows partition to be intact. If I'm to select Guided mode, which uses the "entire disk space", does that mean my Windows will be... gone? Or "entire disk space" in this case refers to the unpartitioned space of the hard drive? Again, silly as it sounds, it still needs clarifying.

- I really sound stupider with every question I ask but here I go: after installation completes, suppose that my Windows is still there, I will be prompted to choose which OS to boot from, right? I did indicate that I still plan to use Windows as my primary OS (until I master Linux, I might have a second thought), thus I would like Windows to boot up by default. Would this happen by itself (as in the CD installs Ubuntu as a secondary OS or it automatically sets Ubuntu to auto-boot?)

I can't wait to get Ubuntu up and running but I need to ask carefully as I have been babysat by Microsoft for years, so Linux environment (primarily command-based as I understand it) is a true challenge for me.

Thanks for your replies.

Cheers,

---

### Post by doomster on 2007-07-06
to begin with , there is no such thing as silly questions. :)
when you install ubuntu, in the boot loader by default ,ubuntu system 
is set to boot up, if nothing else is selected. but boot loader is configurable,
 so i dont thing you will have trouble making windows your default
selection. 
before the install you should check [wiki's photo guide]("https://help.ubuntu.com/community/GraphicalInstall")  , this should help you on selectin partitions and stuff :)
I prefere to manually edit the partition table, to create the partitions needed, without touching the ntfs backup partitions i have :)

to endwith, i havent tried to burn the cd image to a dvd to checck it. I would recommend burning it on a CD , as every DVD recording device around, burns also CD's :}

---

### Post by stalkingwolf on 2007-07-06
You will probably have to use the manual option.  That way you can set up the 3 partitions for ubuntu
pretty easy.  I like to have a seperate partition for /home in addition to / and swap.  As I recall doing it this way
you can store files and configurations and such in  /home and they are not affected if you have to reinstall.

---

### Post by aquavitae on 2007-07-06
Regarding my previous suggestion:  I'm sure you know this, but its much better to backup to cd or dvd than to another hard drive (I suppose I should really follow my own advice here!).  And why put tha page file on a separate drive?  I know its supposed to improve performance, but I can't say I'm ever really noticed the difference.

Anyway, the lnux installation itself won't take 40G, 20G should be more than enough, and you could manage quite comfortably on 10G.  I think the min requirements are 2G.  So you could still install linux to that drive, and keep all your docs on another partition of the 250G drive.  If you're sharing your docs with windows, you don't even need the extra partition.

Hope this helps!

---

### Post by K_Soze on 2007-07-06
I am brand new to linux as well. I just installed KUBUNTU 2 weeks ago with pretty much the same setup as what you have. IF you google XP LINUX DUAL BOOT there is actually a video that shows the guys doing exactly what you're asking.

It helped me and it was pretty easy after you saw the steps. With feisty grub actually took care of all my dual boot worries and I didn't do anything.....


Good luck.

---

### Post by ITdrummer on 2007-07-06
What chipsets and drivers do your wireless cards use? I just went through a week of trying to get my wireless card working.  Not to scare you but if your using a broadcom chipset...good luck.   Not impossible, but definately NOT FUN!

---

### Post by lamchopz on 2007-07-06
OMG! I love all of you! Speedy, to-the-point replies.

To aquaviate: I know backing up data on external media is the best option. However, I dun have a CD/DVD burner (just an iPod 30GB, which is what I use to store all the necessary data for the next reformatting). My bro's computer does have a burner, which is what I'd use for burning the Live CD and the RescueCD. However, I don't like to jump on his computer every time I need to back up something important. That's why I'm fixated on the secondary drive idea. However, I will definitely try out your suggestion and rework my backup scheme.

To doomster: the wiki guide is definitely AWESOME. 

To stalkingwoof: I'm not used to working with commands yet. So I only get half of what you're saying (I get the purpose and conceptual infrastructure but exactly how it works... well, I'm noob).

To K_Soze: thanks, I feel more ready to install than before.

To ITDrummer: I had a Linksys WMP54GR, after some stupid software trials, my computer got problems (thought it's related to the card), I then switched to Belkin usb wireless adapter, and still have the same problems. THus I nailed it down to my computer which is the source of all ills, hence the reformatting.

I'll post back if I have more questions, or... (not fun but) if I have any troubles installling.

Cheers,

---

### Post by kartik2104 on 2007-07-07
hi!
i m an absolute beginner i have managed to install ubuntu on my system of 80gb hard disk having 512 mb of ram  and my processor is 2.8 dual core processor okay.
first of all i m unable to set the refresh rate of my system to 75 hertz its only up to 60 hertz and there are no more options and my screen keep on shaking slightly, to set this up do i have to install drivers, if yes then from where can i get them for intel 945 gccr mother board?
what shall i do to pair up my phone wid my system?
please reply me?
........

---

### Post by doomster on 2007-07-07
you will probably have to install drivers for your Graphics card. what graphic card do you have on your system? 

wether you use Nvidia or Ati chipset  on your graphic system, then [Envy's Script]("http://www.albertomilone.com/nvidia_scripts1.html")  is probably the easiest way to upgrade your drivers to the last official version

---

