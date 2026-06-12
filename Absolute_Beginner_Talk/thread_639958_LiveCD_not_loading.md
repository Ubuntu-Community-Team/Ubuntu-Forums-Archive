---
title: "LiveCD not loading"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by abc006 on 2007-12-13
Hi all, I've got a problem with the LiveCD. I've just decided to (finally) try out ubuntu. I have a vista basic. So, I downloaded v 7.10 and burned it to a CD using InfraRecorder as the instructions said. I restarted the computer with the CD in, shut off and started it, etc., yet it just won't load - it goes directly to the vista login screen like normal. When I run it regularly in vista, it brings up the "Ubuntu 7.10 (DiscTree)" window I assume like normal, so it doesn't seem like there's any problem with the file and/or disc or anything, but then again I'm not sure. Does anyone know what's happening here or if I'm doing something wrong? Thanks a lot for your help in advance.

---

### Post by taurus on 2007-12-13
You need to get into the BIOS and change the boot order from harddrive first to CD-ROM first.

---

### Post by Dark_Stang on 2007-12-13
Edit: Pwnt by ^

Three(at least) things could have happened here...

1. Your computer isn't setup to boot from cd first. You'll have to go into the bios and make sure the cd/dvd drive is set ahead of the hard drive.

2. Bad image/bad cd.

3. iso wasn't burnt properly.

---

### Post by Rocket2DMn on 2007-12-13
Have you checked to make sure that the CD drive is higher up in the boot order sequence than your hard disk?
You can access the BIOS when you reboot the computer - you usually have a second or two at most to enter Setup via some hotkey like F2, F8, F12, ESC, or DEL.  From there you can browse around using the keyboard - make sure the CD drive is above Hard Disk in the boot sequence.

---

### Post by abc006 on 2007-12-13
I'll try that Rocket, thanks.

---

### Post by elliotjreed on 2007-12-13
You need to change the boot order in your BIOS - this usually means pressing esc. F2, F5, F6 or whatever (sometimes tells you at the bottom!)

Change it to boot from CD first...

Then you should be going!

---

### Post by Want A Pie on 2007-12-13
Make sure you burn it to a CD, not a DVD!
and it has to be burnt at 4x, not higher!
(found out them the hard way :P)

---

### Post by abc006 on 2007-12-13
I chaned the boot order and it worked, thanks a lot guys

 Well, Want a Pie, I downloaded 'er at a steady 20x... I guess I'm lucky it's all still in tact. :)

While we're on the subject of... well, ubuntu, I've got a pretty basic question: when you install ubuntu onto your hardrive, A) what will happen to all your existing files/vista installation, and B) will you be able to switch from ubuntu to vista when you want to run programs that you can't run on ubuntu? Thanks again.

---

### Post by Stormspireiv on 2007-12-13
> **abc006 said:**
> I chaned the boot order and it worked, thanks a lot guys

 Well, Want a Pie, I downloaded 'er at a steady 20x... I guess I'm lucky it's all still in tact. :)

While we're on the subject of... well, ubuntu, I've got a pretty basic question: when you install ubuntu onto your hardrive, A) what will happen to all your existing files/vista installation, and B) will you be able to switch from ubuntu to vista when you want to run programs that you can't run on ubuntu? Thanks again.

It really depends on how you set it up.  Most people who just are getting started on Ubuntu from Windows use a dual boot configuration so whenever you start up your computer, you have a choice of Windows or Ubuntu.  This is normally done by shrinking your existing Windows installation and installing Ubuntu in the freed space.  Be careful what you select in the installation, as you could end up wiping your drive if you select the wrong partitioning option.  There are plenty of tutorials available for different set-up's, and I suggest you find one that suits your purposes.

---

### Post by abc006 on 2007-12-13
OK, thanks, I'll check a couple out.

---

### Post by zabien1970 on 2007-12-13
In the 'sticky' section at the top of the absolute beginner talk page the last one has install methods with plenty of links, make sure you read on 'vista' installing since it is different and you need to let 'vista' resize its partition instead of letting the live cd do it, also be carefull installing sice its easy to accidentally erase your windows partition if you make a wrong choice in installing. Just makesure you read up well and take notes so you're prepared and it should be fairly simple.

---

### Post by abc006 on 2007-12-13
So is [this]("http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot&total=39&start=0&num=10&so=0&type=search&plindex=0") all there is to it? If I have, say, 15 or 20  free GB on my hard drive, would I just follow the steps in there and it would run fine with the dual boot?

---

### Post by Dark_Stang on 2007-12-13
> **zabien1970 said:**
> In the 'sticky' section at the top of the absolute beginner talk page the last one has install methods with plenty of links, make sure you read on 'vista' installing since it is different and you need to let 'vista' resize its partition instead of letting the live cd do it, also be carefull installing sice its easy to accidentally erase your windows partition if you make a wrong choice in installing. Just makesure you read up well and take notes so you're prepared and it should be fairly simple.

If you let Vista resize it's partition it's only going to shrink by about half it's size. If you use the partition editor that comes on the 7.10 CD you shouldn't have any problems resizing Vista. Or at least, I didn't for the few times I tested it after the install. And I imagine nobody else did who I gave directions to. If they had problems I'd be getting flamed like crazy by now.

And 15-20 gigs is plenty for Ubuntu.

---

### Post by abc006 on 2007-12-14
OK, two questions...

1. First of all, I looked at this video tutorial:
[http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot&total=39&start=0&num=10&so=0&type=search&plindex=0](http://video.google.com/videoplay?docid=-2369893842637434537&q=ubuntu+dual+boot&total=39&start=0&num=10&so=0&type=search&plindex=0)
which was very handy. However, I then read this tutorial:
[http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon](http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon)
which showed a different selection screen for partitioning the disk than shown in the video tutorial:
[http://images.howtoforge.com/images/gutsy_desktop/pic7.jpg](http://images.howtoforge.com/images/gutsy_desktop/pic7.jpg)
 The howtoforge.com tutorial had a screen shot showing the selections being: using the entire disk - I assume that's deleting all of windows - or manual, which I have no idea how I would set up. However, on the video tutorial, it showed at around 6:05 four different options, including one to partition the disk for a dual boot installation. So, which one will I find on the installation for Gutsy Gibbon and if I need to use manual or something like it, what would I punch in for the same result as showed in the video tutorial?

2. I also read a few other threads where it talked about NTFS-formatted shared data - I assume these are files of your choice which appear both in ubuntu and windows, like My Documents? And if this is the case... how do I go about setting it all up, seeing as I have no idea what NTFS means? Can I do it in the installation process, do I need other programs, how do I choose what files would be shared? Etc.

As you can see, I'm quite clueless with most of this ubuntu stuff, so thanks again for all your help.

---

### Post by abc006 on 2007-12-14
OK, on the LiveCD for 7.10, I ran through the installation stuff until I got to the "prepare disk space" prompt, just so I could see what it said, and it looked like the one on the howtoforge.com tutorial I mentioned right above. Therefore, I assume to partition the disk for a dual boot install, I would have to do something with the "manual" option? And if so, what would that be? Also, if anyone could answer my second question above too, that would be great. Thanks again.

Edit: And, what about Wubi? Does it work and is it a viable option instead of partitioning?

Edit #2: AND, I've been searching around for more tuts, and is this one accurate?
[http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)

---

### Post by abc006 on 2007-12-15
Sorry for the triple post, but I'm just trying to get this answered, since because of the massive size of the entire forum, if you wait just overnight, your thread suddenly goes to page 10 with hardly any chance of it getting noticed. Kind of off-topic, but perhaps you should create sub-forums within the aboslute beginner forum so that threads don't get hidden so fast. 

Anyway, if anyone could answer the questions above, I'd really appreciate it. Thanks so much. :)

---

### Post by Stormspireiv on 2007-12-15
> **abc006 said:**
> OK, on the LiveCD for 7.10, I ran through the installation stuff until I got to the "prepare disk space" prompt, just so I could see what it said, and it looked like the one on the howtoforge.com tutorial I mentioned right above. Therefore, I assume to partition the disk for a dual boot install, I would have to do something with the "manual" option? And if so, what would that be? Also, if anyone could answer my second question above too, that would be great. Thanks again.

Edit: And, what about Wubi? Does it work and is it a viable option instead of partitioning?

Edit #2: AND, I've been searching around for more tuts, and is this one accurate?
[http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)

This youtube video is an excellent tutorial to dual boot.  The only thing that it leaves out is putting your home folder on a separate partition (and that is optional, yet highly recommended).  I do recommend, as the tutorial says, that you shrink your windows partition in Gparted first. This makes the installer alot less risky to use.

Edit: I am glad you are researching this before an install.  Way too many people just slam in the Live CD and install blindly; then they come back wondering why Windows and all their data is gone.

---

### Post by abc006 on 2007-12-15
How would I go about putting the home folder in the seperate partition? Does this have to do with "NTFS-formatted shared data" - and again, I assume that means those are files are viewable in both ubuntu and windows?

---

### Post by abc006 on 2007-12-15
Anybody? Thanks again.

---

### Post by Stormspireiv on 2007-12-16
You have to do manual partitioning for a home folder on a separate partition.  After shrinking your Windows partition in Gparted, you can go in the installer and select manual partitioning.  There you can create your partitions. You want:
1) A home partition. This should be large enough to hold all your personal files such as music, videos and documents as well as the configuration files for programs. (in the create partition dialog, it should have an option to select "/home" without quotes )
2) A root partition. This should be large enough to hold the OS (2gb) as well as any other programs you want to install. If you want a lot of native linux games and/or a lot of programs, give this partition plenty of space.  (this partition should be designated "/" without quotes)
3) A swap partition.  This should be around one to two times your RAM size. (this partition should be designated swap)

This set up is much more advanced than the simple "guided - use largest continuous free space", but it is extremely useful.  With your home folder on a separate partition, you can replace the entire OS with another linux distribution or a new version of Ubuntu and still have all your personal files and configuration files intact.  Sometimes upgrading to the new Ubuntu release breaks Ubuntu (or breaks some of the programs you have installed) - this way you can always replace the OS instead of "upgrading".

Also, if you don't put the home folder in its own partition, you can always move it there at a later date, but that is an involved (and quite risky) procedure.

---

### Post by abc006 on 2007-12-16
Great, thanks so much! Just one question - would the swap partitoin be just "swap" or something like "/swap"?

---

### Post by Stormspireiv on 2007-12-16
In the manual partitioning screen, it should show all your hard disks and each partition in that hard disk. You windows partition should be of the type ntfs. DO NOT MESS WITH IT. You should have already shrunk it in Gparted to have extra room. For the new partitions, make them all type: ext3 except for the swap which will be type: swap.

For the non swap partitions, their mount point will be as I said in previous post. For the home partition, it should be /home and for the root partition it should be /

Before messing with this, there is still a chance you could mess up your windows partition because it is possible to format the entire hard disk (not just the partition) from this screen. I suggest you back up your critical files on Windows.

---

### Post by abc006 on 2007-12-17
OK, thanks a lot for the advice. I'll hopefully get on it soon. :)

Actually, just *one* more question - if I can access all my files on windows from ubuntu, then the /home partition would be for only files stored on the ubuntu side of things, right? So, would I actually even need a large amount of space for "/home" if I planned on saving and accessing most files from the windows documents folder? (i.e. the /home equivalent.)

---

### Post by Stormspireiv on 2007-12-18
You are exactly correct. If you plan on saving most of your stuff to your windows partition, then you don't need a very big /home partition.  That was the way I was doing it until a couple months from now.

---

### Post by mondy on 2007-12-18
definately bad image

---

