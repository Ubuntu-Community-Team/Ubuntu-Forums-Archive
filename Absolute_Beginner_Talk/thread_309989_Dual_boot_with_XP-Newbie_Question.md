---
title: "Dual boot with XP-Newbie Question"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by vikingprincess on 2006-11-30
**Background:**
Ideally I'd like to drop XP right now... 
But I have A LOT of Windows software that I really don't want to replace with Linux versions due to the time/expense involved.. 

I am a techie - I work in IT, now management, previously dev. However unfortunately I have only very limited experience of Linux/Unix and have never used a GUI version. 

So my question is if my system is suitable for doing dual-boot, and what specifically to bear in mind for my particular system.
(I will of course find a generic thread for setting up XP/Ubuntu dual boot once I am certain I want to go ahead.)

My only experience with dual-boot to date was running NT4/win98 around the millenium while doing second line tech support at Sybase. 

**System spec: **
[LIST]
[*]AMD 3700 single CPU, 
[*]2 internal hard drives, 
[*]3GB RAM.
[/LIST]

(don't want to upgrade anything right now on this system  budgetgirl $$$.. :-)

[LIST]
[*]Drive A) 60GB. It now serves as data storage. One partition
[*]Drive B) The 250 has two partitions, C (system) is 60Gb and D (storage + programs) is 190GB. 
[*]Drive C) 320 GB External Drive.
[/LIST]
 
There is 25-50% empty space on each partition. 

**Important Questions: **
[LIST=1]
[*]What partition / drive is best for putting Ubuntu on? 
[*]Any problems with my spec? 
[*]Would I get a dual boot Bios screen giving me the option to choose what system to launch?
[*]Would I see all my drives and data in Ubuntu?
[/LIST]

**Extra-currricular questions: **
[LIST=1]
[*]Are Dreamweaver and Photoshop available for Linux? If not, what are people using?
[*]Is it feasible to be Linux-only at home? particularly as work, friends etc are Windows... ( I am hoping to be able to drop Microsoft products altogether if possible)
[/LIST]

Any other tips appreciated, hope you can help! 
JO

---

### Post by antharr on 2006-11-30
You are not being serious when you say this is your budget system, right?

You will have no problem running any version of Ubuntu.

---

### Post by aswells on 2006-11-30
For every Windows program, there is a linux alternative. Some of them arent as well polished as their windows counterparts, but you can certainly get things done. 

As for the feasibilty of being linux-only in a dominantly windows invironment, I am a college student attending UofH(go cougs) and have been windows free since my enrollment.

---

### Post by scc4fun on 2006-11-30
> **vikingprincess said:**
> **Background:**
Ideally I'd like to drop XP right now... 
But I have A LOT of Windows software that I really don't want to replace with Linux versions due to the time/expense involved.. 

I am a techie - I work in IT, now management, previously dev. However unfortunately I have only very limited experience of Linux/Unix and have never used a GUI version. 

So my question is if my system is suitable for doing dual-boot, and what specifically to bear in mind for my particular system.
(I will of course find a generic thread for setting up XP/Ubuntu dual boot once I am certain I want to go ahead.)

My only experience with dual-boot to date was running NT4/win98 around the millenium while doing second line tech support at Sybase. 

**System spec: **
[LIST]
[*]AMD 3700 single CPU, 
[*]2 internal hard drives, 
[*]3GB RAM.
[/LIST]

(don't want to upgrade anything right now on this system  budgetgirl $$$.. :-)

[LIST]
[*]Drive A) 60GB. It now serves as data storage. One partition
[*]Drive B) The 250 has two partitions, C (system) is 60Gb and D (storage + programs) is 190GB. 
[*]Drive C) 320 GB External Drive.
[/LIST]
 
There is 25-50% empty space on each partition. 

**Important Questions: **
[LIST=1]
[*]What partition / drive is best for putting Ubuntu on? 
[*]Any problems with my spec? 
[*]Would I get a dual boot Bios screen giving me the option to choose what system to launch?
[*]Would I see all my drives and data in Ubuntu?
[/LIST]

**Extra-curricular questions: **
[LIST=1]
[*]Are Dreamweaver and Photoshop available for Linux? If not, what are people using?
[*]Is it feasible to be Linux-only at home? particularly as work, friends etc are Windows... ( I am hoping to be able to drop Microsoft products altogether if possible)
[/LIST]

Any other tips appreciated, hope you can help! 
JO

*Disclaimer: I am not an expert in Windows or Linux*

Your specs look fine for installing Ubuntu as dual-boot. What will happen when you install Ubuntu is it will ask you to create a partition(s) for it to run in. You will need to decide how much space you want to set aside for Ubuntu Linux to run in. During installation you can shrink a partition to create space for Ubuntu. It is recommended that you defragment whichever partition you want to shrink before changing it. Also, back up any data on that partition as there may be data corruption when you change any partition.
Yes, you'll be able to install GRUB boot loader that will allow you to choose which OS you want to start up.
It is definitely feasible to be linux-only at home. You won't be able to run every program, but there are many alternatives in linux. For example you could use a program such as NVU in place of Dreamweaver or The GIMP or Picasa for Linux in place of Photoshop.

---

### Post by Rontie on 2006-11-30
if your a dedicated to the idea of getting rid of windows then sure, its fully possible, but you might find it best just to dual boot and boot into windows when you needs to, you certainly seem to have enough space to do so. 

No adobe doesn't do Linux, but there certainly are Linux alt's, for photoshop try out gimp maybe and i used dreamweaver when i was on Windows, now i use Nvu. Its not as fancy but it does the job and i like it fine. 

And to answer your 'important questions', Yes!

Ubuntu will load fine on your system (though not knowing what other hardware you have.. i.e it might not be perfect out of the box). You will have the choice of course as to which you will boot in with the grub. And you can put it on whatever one which you want. If you are dual booting make sure you don't have them on the same....

Linux if free, most of its software is free so if there isn't going to be much expense involved if that is one of you decision makers. Just go for it

okay

---

### Post by PurplePenguin on 2006-11-30
Upgrade?  Oh my... no need for that.  Ubuntu is going to FLY on your system! :)

To answer some of your questions:

Yes, upon boot you'll be able to choose which operating system you want to run.

Yes, under Ubuntu, you'll be able to see all of your drives.  You won't, however, be able to see your linux drives while you're in Windows.

I'm another who is running Linux only right now.  I had Windows on my system in order to play a couple Windows games, but now that I've discovered Nexuiz, that's no longer a problem. :)  It's no problem running linux in a windows world... you can use Gaim to talk with your friends/coworkers on MSN, Gimp instead of Photoshop, OpenOffice instead of MS Office, etc.

---

### Post by docshawnc on 2006-11-30
Just a comment regarding seeing Ubuntu drives in your windows system - yes you can do this by making them Samba shares.  These then appear to be windows drives from within XP.  You will also want to use ntfs-3g to load your ntfs drives when starting Ubuntu - this will allow you to write to the windows partitions as well as read from them.

You may want to also take a look at VM Server which will allow you to run XP inside of a total Linux box (as opposed to dual booting)

---

### Post by vikingprincess on 2006-11-30
Thanks for the replies so far! 
[I]
Well I am aware I have a lot of RAM, and storage.. But actually the processor is struggling a lot in Windows. I often find myself waiting for it, or killing 100% processes.. I'd like a dual proc...  but it's not in the budget. Tip for having a good machine: Build it yourself, buy compatible components and upgrade as you go... ;-)  ) 
[/I]

Somebody mentioned having to PARTITION part of the drives for Linux. But how does that work in my situation? 

For example, In Partition Magic, what would I have to do? 'Slice up' existing partitions? 

I have already formatted all the space on my disks. 
And created partitions. 

Although there **is** free space, Windows doesn't like it if fill up partitions over 80%. So in reality I don't have that much space to use for Ubuntu (?) 
JO

---

### Post by sigge on 2006-11-30
Regularily there is no _expense_ in GNU Software, but OK... :)


You being a techie, and your system being what it is, you are ready for downloading the LiveCD Ubuntu. Burn it to a cd, and boot from it. This way you can try out most of the internet, office and productive software, without installing or partitioning. Then if you like it, run the install wizard from the desktop link.

Dualbooting has come a long way since 99-2K. I remember how bad it was back then, with LILO... But Ubuntu uses Grub for bootloading, and is fairly configurable, I gather. I don't have much experience though... I'm running linux only since 200X.

Both your internal drives should do fine. Not too shure about the external one though... Still, I might be wrong.... Someone correct me if I am :)

There is no problem with your specs, as far as I can see. Everything stands and falls on your grafics card, you never described it... :( But everything else is Green for Go with bells and whistles on them.

You will get a menu on boot time, if this is what you setup during install.

In my experience, there is little trouble accessing your windows data. this is also set up in the install, btw.

We don't do Photoshop in Linux. We use the Gimp! It rocks better than PS, whatever my wife wants to tell you... :) No real Dreamweaver Challenger as of yet, but check out Screem and NVU. And then there's always handcoding... Mmmmmmmmm....](*,) 

A linux only home is quite doable. Check out all the different stuff there is, like MythTV, RythmBox, Democracy TV, and more for multimedia, etc. All the different planning and project software as well as regular software, such as openoffice.org, the Evolution PIM. Games are coming more and more every day. Commercial games, GNU games, take your pick... Projects such as Wine make it possible to run M$ games and apps on linux. Check that out in reference to DW and PS.

Hope I made some sense, and that you can enjoy linux. Good luck.

---

### Post by ninjaPants on 2006-11-30
Re: partitioning...
I'd probably make space on your "drive a" How much depends on how much you think you'll use Ubuntu. For a while I was dual booting (and then windows coughed up a lung and I decided to swich back over to Ubuntu only) with about 10gb of my drive for Ubuntu divided into 1gb for swap, 4gb for /home and 5gb for root. This was enough to install everything I wanted (made the partitions pretty full though). I also made a 1gb fat32 partion to share between Windows and Ubuntu. I stuck documents I wanted to edit in the other OS there. 

You'll want to backup everything on the harddrive you're partitioning (as someone already said). I'd pass up the Ubuntu included partitioner for the GParted LiveCD ([link.]("http://gparted.sf.net/")). It's the same program but usually more up to date as opposed to whats on the Ubuntu disc. 

If you want to run windows programs under Ubuntu (with wine, etc), you'll want to make enough space to install them on the Ubuntu partition. 

If you can eat up half of that 60 GB drive I'd go with 3GB swap at the start of the drive, followed by 40 for root and 17 for home. A lot of people have very strong opinions about how you should partition a drive, and it scared me off for quite a while. Chances are whatever you allot will work. A good rule of thumb is to have your swap space equal the size of your RAM (or at least I've been told).  Since your data partion will be moved to the back of the drive, you might just backup all that data to your external drive, make a new partion for the data (remember: fat32 can be read by both OSes) and restore that data to the new partition. Resizing and moving can be very destructive, especially if it's a ntfs partition.

Someone mentioned using ntfs-3g to write to windows partitions. Write support for ntfs under linux is pretty new and so I'd only write to windows partitions if it's absolutely necessary. I've screwed up ntfs partitions before and it's really frustrating. This probably has made me overly cautious, but if there's important stuff on those drives you should probably be pretty dang cautious.

Hope this helps. Feel free to PM me if I've been as terribly confusing as I think I may have been.

---

### Post by Oki on 2006-11-30
&#8221; We don't do Photoshop in Linux. We use the Gimp! It rocks better than PS&#8221;

This is not true at all; Gimp can&#8217;t work in 16bits mode, do not support colour management, no actions, not user friendly and so on&#8230; Stop saying Gimp is better then PS &#8211; PS is the king! The good news is that those lacking futures will be fixed in a later update. I am looking forward to that. PS 7 can be used under Linux via Wine, but not newer versions. 

For image applications under Linux take a look at this thread; [http://ubuntuforums.org/showthread.php?t=293798&page=4](http://ubuntuforums.org/showthread.php?t=293798&page=4)

For other applications for Linux(compared to Windows) take a look at this one; [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by Zaen on 2006-11-30
This is kind of going off on a different idea, but it is possible on a lot of computers to boot off of usb, so if you wanted to, your pc could stay the same, with linux on the removable hard drive. This would, however slow it down, though it would probably be faster than Windows still.

good luck!

---

### Post by vikingprincess on 2006-11-30
Wow, thanks for those comprehensive pieces of advice, Sigge & Ninja.. Thanks for the tips about alternative software.
(Just realised I will have to keep some kind of Windows around as I am dependant on MS Project for work. )

I am going to re-read all this and put together a 'plan of action' for completing the dual boot. I'll ask for help to verify that I got it right. I think I'll do a new post for that.

About the Graphics card: It's the best available spec for AGP i believe, so that does not worry me. It's a nVidia GeForce GS7800.

[message in Swedish for Sigge ; Tusen tack! Hoppas Du kan kolla min nästa post också!:rolleyes: ]

---

### Post by ragadanga63 on 2006-11-30
I agree with Oki.  GIMP is never better than Photoshop.  However, GIMP maybe sufficient to your needs.  In my case, I am a power user of Photoshop and does CMYK color separation printouts using prepress equipment and laser printers for tshirt printing.  No way GIMP will do the job for me.  Photoshop and Coreldraw are the only two applications holding me back from a complete jump to UBUNTU.  

Vikingprincess, your system will fly with Ubuntu.  I run Ubuntu on an AMD K62 500MHz(circa 1996) and it runs like a dream.  Also if you play windows format media on Ubuntu, you may need to install additional codecs which do not come with the box- a pretty perflexing job for a newbie but with diligent reading, is doable.

Good luck.

---

### Post by serentaius on 2006-12-01
I would just like to start by saying that I find it strange that you're having troubles running windows with your system. Is the processor an AMD XP 3700+? I've got a AMD Athlon 64 3400+ (over-clocked to 2.7 GHz athankyou!) and windows flies. Ubuntu is going to go about twice as fast on your comp.

---

### Post by gn2 on 2006-12-01
Here's my dual-boot suggestion: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Better than that would be to use VMWare or Parallels and run Windows as a virtual PC inside a Linux host.

---

