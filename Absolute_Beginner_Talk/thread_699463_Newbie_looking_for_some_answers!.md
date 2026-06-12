---
title: "Newbie looking for some answers!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by blackbinary on 2008-02-17
Total newbie to linux here, thought Ubuntu looked good and wanted to give it a try.

I've read all the relevent guides I could find, so I have some sort of a fuzzy concept. I have yet to install or download so im sure once I do so I'll have a better grasp of things. 

Currently im running windows xp, and really can't get rid of it, too many programs I need. I'm looking into setting up a dual-boot of Ubuntu with Windows so I can run both. First off, are there any forseeable problems with setting my system like this? all my files are NTFS, is that a problem? I've got an 80gig harddrive with just windows and a little extra on it, then a 320gig harddrive for just storage, with 170gigs or so free, im thinking of partitioning this for ubuntu. 

So, I haven't had really any experience using a CLI besides the occasional ipconfig in windows. Therefore, while im not against using it, the more GUI elements the better. From what I've read and seen, it appears that I may have to do a few things in the CLI while setting up, but after that its not really needed, and I can learn at my own pace. 

I've got a pretty robust system (AMD Athlon X2 5200+, 3Gb RAM, nVidia 7900GS), but even still windows is a bit sluggish. I don't think i could get it to boot or shut down any faster, even after the tweaking i've done. 

I can't seem to decide what is best for me, Xubuntu, Ubuntu, or Kubuntu. I thought Xubuntu sounded good because it was light-weight and fast. I only want to use linux for firefox, IM, maybe word processor, music player. Really basic stuff that all of them have. At this point I just want to jump in and explore and learn, So i'm not really concerned with alot of other programs which I can just boot back into Windows for. 

So... lets see if I can come up with some questions:

1) How much should I expect to have to use the CLI? Can i avoid it for every day use?
2) Which version of Ubuntu should I use? I'm looking for something speedy. 
3) Are the any problems with having Ubuntu and Windows in a dual-boot configuration? 
4) Files are in NTFS, is this a problem?
5) Drivers already installed for video card, etc. through windows, will those need to be reinstalled?
6) This fits in with #4, but Will be able to acess all my data (was thinking mostly MP3s)


Thanks for any replies I get. I'm searching for some info on dual-booting now, so if you like you can post on that subject too. Hopefully I'll be running with the pengiun by tonight :)! 


(heh, hopefully this is in the right forum, thanks again!)

---

### Post by sb12 on 2008-02-17
> **blackbinary said:**
> Total newbie to linux here, thought Ubuntu looked good and wanted to give it a try.

I've read all the relevent guides I could find, so I have some sort of a fuzzy concept. I have yet to install or download so im sure once I do so I'll have a better grasp of things. 

Currently im running windows xp, and really can't get rid of it, too many programs I need. I'm looking into setting up a dual-boot of Ubuntu with Windows so I can run both. First off, are there any forseeable problems with setting my system like this? all my files are NTFS, is that a problem? I've got an 80gig harddrive with just windows and a little extra on it, then a 320gig harddrive for just storage, with 170gigs or so free, im thinking of partitioning this for ubuntu. 

So, I haven't had really any experience using a CLI besides the occasional ipconfig in windows. Therefore, while im not against using it, the more GUI elements the better. From what I've read and seen, it appears that I may have to do a few things in the CLI while setting up, but after that its not really needed, and I can learn at my own pace. 

I've got a pretty robust system (AMD Athlon X2 5200+, 3Gb RAM, nVidia 7900GS), but even still windows is a bit sluggish. I don't think i could get it to boot or shut down any faster, even after the tweaking i've done. 

I can't seem to decide what is best for me, Xubuntu, Ubuntu, or Kubuntu. I thought Xubuntu sounded good because it was light-weight and fast. I only want to use linux for firefox, IM, maybe word processor, music player. Really basic stuff that all of them have. At this point I just want to jump in and explore and learn, So i'm not really concerned with alot of other programs which I can just boot back into Windows for. 

So... lets see if I can come up with some questions:

1) How much should I expect to have to use the CLI? Can i avoid it for every day use?
2) Which version of Ubuntu should I use? I'm looking for something speedy. 
3) Are the any problems with having Ubuntu and Windows in a dual-boot configuration? 
4) Files are in NTFS, is this a problem?
5) Drivers already installed for video card, etc. through windows, will those need to be reinstalled?
6) This fits in with #4, but Will be able to acess all my data (was thinking mostly MP3s)


Thanks for any replies I get. I'm searching for some info on dual-booting now, so if you like you can post on that subject too. Hopefully I'll be running with the pengiun by tonight :)! 


(heh, hopefully this is in the right forum, thanks again!)

normally you wont have to use cli, no. xubuntu is the faster of the three, but with your specs all should be quick. dual-booting is fine. ntfs-3g will let you write to ntfs partitions. you may have to play with it to get the nvidia card working, there are howtos available. you will be able to access your files, yes

---

### Post by drs305 on 2008-02-17
1) CLI is much more convenient for some things, but you won't have to use it often. When you do, you will probably be able to cut and paste the command from something you've read on this forum.

3) No problem. GRUB will allow you to pick the system you want to boot into at startup.
4) NTFS is not a problem. In fact, I believe the capability to read NTFS is native to Gutsy.
5) Linux has it's own drivers. If you don't have really old hardware it should not be a problem. If you are concerned about specific items, you can seach this forum with the model number.
6) No problem.

Welcome to ubuntu!

---

### Post by tact on 2008-02-17
First things first... download the "desktop" live CD and burn it to a CD and boot from that liveCD.  No need to install straight away.  

Booting from the live CD won't change any files on your system at all and it gives you a chance to "test drive" ubuntu and see that all your hardware still works just fine.    If all your hardware  is supported out of the box then y just to use firefox, IM and play MP3's you will never need to use the CLI at alll.

Only when you are happy all your hardware works fine ...then consider hittint the "install to HDD" icon on the desktop.

This will guide you to install and set up dual boot system.  Assuming all your hardware was supported out of the box, and the dual boot installs correctly - then you will not need to reinstall aanything in windows.  It will all be there and work later.

Yes your files on the NTFS drives will all be accessible.

---

### Post by jan quark on 2008-02-17
> 1) How much should I expect to have to use the CLI? Can i avoid it for every day use?

yes
> 
2) Which version of Ubuntu should I use? I'm looking for something speedy. 

everything is faster than windows :lolflag:

joke, ubuntu is fast, xubuntu is faster

> 
3) Are the any problems with having Ubuntu and Windows in a dual-boot configuration? 

when you install ubuntu after windows there are no problems

see this nice site for dual booting
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

> 4) Files are in NTFS, is this a problem?

no ubuntu supports ntfs reading with this applcaition ntfs-3g
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

> 5) Drivers already installed for video card, etc. through windows, will those need to be reinstalled?

ubuntu will be installed on a separate partition, so there is no connection whatsoever between the windows drivers and linux drivers

ubuntu support for graphic audio and wireless has greatly improved over the past few years so if something is not detected out of the box the installation is usually painless


> 6) This fits in with #4, but Will be able to acess all my data (was thinking mostly MP3s)

of course you can mount your windows partitions in ubuntu and access the files

---

### Post by zerhacke on 2008-02-17
> **blackbinary said:**
> 
1) How much should I expect to have to use the CLI? Can i avoid it for every day use?
2) Which version of Ubuntu should I use? I'm looking for something speedy. 
3) Are the any problems with having Ubuntu and Windows in a dual-boot configuration? 
4) Files are in NTFS, is this a problem?
5) Drivers already installed for video card, etc. through windows, will those need to be reinstalled?
6) This fits in with #4, but Will be able to acess all my data (was thinking mostly MP3s)


1.  There's no real need to use the CLI in Linux anymore.  Yes, there are certain applications that are CLI only but the vast majority of programs for Linux have GUIs for them now.  Even updating your system can be done by the GUI anymore.

2. I find the basic Ubuntu-Gnome to be quite speedy even on my old laptop with just under 256MB RAM (thank you shared memory architecture).  I run a 1.6Ghz laptop at more than acceptable speeds.  If you REALLY want to squeeze out all the speed you can with a system Xubuntu can do well.  You might even want to look into Geubuntu, which is Enlightenment DR17 on Ubuntu which is a blend of the power of Ubuntu with the speed of E.

3. Not at all since you're on XP.  I've heard that Vista doesn't like to have its partition resized by Ubuntu but this is not an issue as you're not on Vista.

4. You'll want to install ntfs-progs ntfs-3g and ntfs-config which will allow you to mount your NTFS partitions to Ubuntu easily without going to the CLI which you said you do not want to use.

5.  You'll find that a default install of Ubuntu or any derivative will find 99.999% of all the drivers you need.  If you have an ATI or nVidia video card you'll need to do a little more work but don't mistake that for trouble.  It's quite easy to install those drivers anymore.

6.  Yes, once you use ntfs-3g and related software to mount your NTFS partitions you can actually read AND write to the NTFS partitions, so you'll easily be able to get ahold of your MP3s and what have you.

---

### Post by blackbinary on 2008-02-17
Wow, this forum is awesome, i didn't expect so many replies so soon.

So, i've watched a few videos of guys dualbooting ubuntu and xp. Now, what i've noticed is they do this off a fresh harddrive with no data. Can i partition the extra space in my 320 gig drive for xubuntu(keeping the data I already have intact!)?

Also, if I understand this correctly, i don't need another partition to keep the files I want to use with Xubuntu? E.g. the files already on my 320gig drive can co-exist with any files for linux without a problem?(Both windows and Xubuntu are fine with this?)

I'm downloading the live CD now, then im going to boot into xubuntu and play around a bit. 

Thanks for the help guys, one quick last question.

This video: [http://www.youtube.com/watch?v=684OLRsTrrs](http://www.youtube.com/watch?v=684OLRsTrrs)

looked particularly cool, as far as the GUI goes. I'm aware that most if not all of the effects are from beryl, so I was wondering if beryl is free, and/or does it work on Xubuntu? 


--Another Edit: 

That reminds me, some videos created a swap file, what does this do in regards to dualbooting xp and xubuntu? 
Also, if I download NTFS-3G, do i need anything besides that to have full ability to read/write NTFS files? 

Other then that, seems like I'm ready to rock :)!

---

### Post by sb12 on 2008-02-17
> **blackbinary said:**
> Wow, this forum is awesome, i didn't expect so many replies so soon.

So, i've watched a few videos of guys dualbooting ubuntu and xp. Now, what i've noticed is they do this off a fresh harddrive with no data. Can i partition the extra space in my 320 gig drive for xubuntu(keeping the data I already have intact!)?

Also, if I understand this correctly, i don't need another partition to keep the files I want to use with Xubuntu? E.g. the files already on my 320gig drive can co-exist with any files for linux without a problem?(Both windows and Xubuntu are fine with this?)

I'm downloading the live CD now, then im going to boot into xubuntu and play around a bit. 

Thanks for the help guys, one quick last question.

This video: [http://www.youtube.com/watch?v=684OLRsTrrs](http://www.youtube.com/watch?v=684OLRsTrrs)

looked particularly cool, as far as the GUI goes. I'm aware that most if not all of the effects are from beryl, so I was wondering if beryl is free, and/or does it work on Xubuntu? 

Other then that, seems like I'm ready to rock :)!

you can repartition your 320gb drive, yes.  Jusr make sure to read carefully so you do not format the entire drive on accident.  you can use an existing partition to share files between ubuntu and windows, yes.  beryl/compiz is free and in the repos, it will work with xubuntu

---

### Post by seventhc on 2008-02-17
one note, when installing ubuntu[COLOR=Red] please do read the screens, especially step 4[/COLOR]
so you don't end up deleting windows. It is very straight forward but for some reason to many people just click next without actually reading whats on the screen in front of them.
Dual booting is a breeze as long as you pay attention during the install.:)

---

### Post by blackbinary on 2008-02-17
Also, whats the main difference a user would see between Xubuntu and Ubuntu?

---

### Post by drs305 on 2008-02-17
Give some thought to how you want to set up your partitions. As a minimum, you will need a swap and a root partition. Many users prefer having a separate home partition as well. For some thoughts on how to partition your ubuntu setup:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Lots of other good stuff there as well.

Make sure you defrag your windows partition before creating any new ones from the extra space!

---

### Post by sb12 on 2008-02-17
the only real difference between ubuntu and xubuntu is the GUI and some of the programs which are installed.  however, you can later install gnome or kde on top of your xubuntu installation, they are all based on the same kernel

---

### Post by blackbinary on 2008-02-17
Ok, after taking a look at that partition guide, I was thinking this:

I have one 320gig harddrive with 170gig free

I have one 80gig harddrive with 30gig free

So, i thought I would simply partion the 80gig. Install ubuntu or xubuntu on a partition of 20gig(is that fine, or smaller, or larger needed?). Then i can keep my 320 as is in NTFS, probably add a small partiton for /home (though I won't put much if anything there). 


Sound good?

---

### Post by sb12 on 2008-02-17
> **blackbinary said:**
> Ok, after taking a look at that partition guide, I was thinking this:

I have one 320gig harddrive with 170gig free

I have one 80gig harddrive with 30gig free

So, i thought I would simply partion the 80gig. Install ubuntu or xubuntu on a partition of 20gig(is that fine, or smaller, or larger needed?). Then i can keep my 320 as is in NTFS, probably add a small partiton for /home (though I won't put much if anything there). 


Sound good?

20gb should be fine, I would not put the home partition on a different drive then / though, personally

---

### Post by Tyke91 on 2008-02-17
for the best results, you should have a 15-20 root partition (/) all of your personal data will go in home, but if you have that huge music hard drive you can actually mount that INSIDE your home partition to make it act as a single folder. it'l be like having a 5 gig home partition that has a secret 350 gig music folder on the inside :)


both Kubuntu and Ubuntu look prettier than Xubuntu does, but xfce(xubuntu) is faster than KDE (kubuntu) or GNOME(Ubuntu).

---

### Post by sb12 on 2008-02-17
> **Tyke91 said:**
> for the best results, you should have a 15-20 root partition (/) all of your personal data will go in home, but if you have that huge music hard drive you can actually mount that INSIDE your home partition to make it act as a single folder. it'l be like having a 5 gig home partition that has a secret 350 gig music folder on the inside :)


both Kubuntu and Ubuntu look prettier than Xubuntu does, but xfce(xubuntu) is faster than KDE (kubuntu) or GNOME(Ubuntu).

not necessarily, gnome and xfce look pretty much the same except xfce ie sleaker

---

### Post by jaytek13 on 2008-02-17
> **sb12 said:**
> 20gb should be fine, I would not put the home partition on a different drive then / though, personally

There is really no reason not to put the /home partition on a separate drive. In fact, there are actually some benefits to doing so, such as if you like to do a clean install when a new distribution version comes out it ensures you will be able to keep your home directory while doing the install bypassing the need to create a backup.

---

### Post by blackbinary on 2008-02-17
Alright. I'm almost finsihed downloading Ubuntu 7.10 amd64 - that sounds like its the right one for a dual core 64-bit amd64x2 processor. Figured i'd go with Ubuntu since it seems to be the more common one, if I feel the need for it to be faster, then I'll switch over to Xubuntu. At this point im just going to try running it live, see how i like it (though i know it'll be slower).

---

### Post by ace007 on 2008-02-17
a few tips:

1.) Defrag your 80 gig partition, assuming thats the one Ubuntu will be installed on.  If you dont defrag it the resizing of the partition wont work.  This is because of windows fragmented files scattered around the drive.  You must defrag so that the area of the partition you are resizing doesn't have any data on it (the fragmented files which are scattered).

2.) When running the LiveCD, under the System Menu go to administration and then to partition editor.  This is the GUI that will allow you to resize the NTFS (windows) partition.  You will not have the ability to resize the partition during the install utility.  

2a.) You best bet is to select the partition to be resized and to remove the last 20000 MB (20GB).  Althougth Linnux can easily fit on 5 GB of drive space.

2b.)  Turn that last bit of raw unpartitioned space into 2 partitions.  One is the place the Linux root will go, "ext3" style.  But leave enough space for a "swap" style partition that is equal to the amount of RAM you have.  Or 1 GB should be plenty.

3.) When installing **[COLOR="Red"]PAY ATTENTION TO STEP 4[/COLOR]**.  Make sure you choose the partition you created (ext3), dont select use whole drive.

Good Luck! You'll wonder why you ever stayed with windoze.  

PS - look into installing WINE in ubuntu.  It is a binary layer that can run many windows applications from Ubuntu (But not all)

---

### Post by blackbinary on 2008-02-17
Thanks Ace, that helps alot. However, i've already looked into WINE, and many applications i need to run just don't have support (nor ever will i'm afraid).

---

### Post by Tyke91 on 2008-02-17
> **ace007 said:**
> a few tips:

1.) Defrag your 80 gig partition, assuming thats the one Ubuntu will be installed on.  If you dont defrag it the resizing of the partition wont work.  This is because of windows fragmented files scattered around the drive.  You must defrag so that the area of the partition you are resizing doesn't have any data on it (the fragmented files which are scattered).

2.) When running the LiveCD, under the System Menu go to administration and then to partition editor.  This is the GUI that will allow you to resize the NTFS (windows) partition.  You will not have the ability to resize the partition during the install utility.  

2a.) You best bet is to select the partition to be resized and to remove the last 20000 MB (20GB).  Althougth Linnux can easily fit on 5 GB of drive space.

2b.)  Turn that last bit of raw unpartitioned space into 2 partitions.  One is the place the Linux root will go, "ext3" style.  But leave enough space for a "swap" style partition that is equal to the amount of RAM you have.  Or 1 GB should be plenty.

3.) When installing **[COLOR=Red]PAY ATTENTION TO STEP 4[/COLOR]**.  Make sure you choose the partition you created (ext3), dont select use whole drive.

Good Luck! You'll wonder why you ever stayed with windoze.  

PS - look into installing WINE in ubuntu.  It is a binary layer that can run many windows applications from Ubuntu (But not all)

actually, defragging your partition shouldn't move all the files to the front, it will just make them more cohesive and easier to move as a group so while it isn't necessary, it is reccomended.

I second the motion to PAY CLOSE ATTENTION TO STEP 4!!!!!!!!!!!! make sure you've made backups of all your files

---

### Post by ace007 on 2008-02-17
> **Tyke91 said:**
> actually, defragging your partition shouldn't move all the files to the front, it will just make them more cohesive and easier to move as a group so while it isn't necessary, it is reccomended.

I second the motion to PAY CLOSE ATTENTION TO STEP 4!!!!!!!!!!!! make sure you've made backups of all your files

Thanks Tyke for clearing that up.

---

### Post by blackbinary on 2008-02-17
Well, just fiddled around with it on my laptop (was out of dvds and my main computer doesnt have a cddrive). 

Seems pretty dang intuitive, knew how to get around, it was all pretty easy. 

Wasn't hooked to the internet though, so couldnt download certain plugins drivers programs etc. But that is fine. 


Anyways, as far as I see it this is how I will install on computer

Defrag both drives
Make partition on 80gig, 20gig big. 
Make partition of 1gig on the 80gig drive for swap (though I don't think i even need a swapfile unless linux is different from xp in that regard)
Make partition on 320gig drive, 5 gigs big(dont plan on putting anything in here really)
Make that partition /home
install ubuntu from dvd
install drivers etc. 
install NTFS-3G

After that, i should be able to acess the files on my 320gig drive properly, and all my drivers should be up to date. 

Sound correct?

---

### Post by Tyke91 on 2008-02-17
to save your windows data, i would recommend just installing the entire thing on the large partition (that way you can get more space if you decide that you like ubuntu more)

my recommended setup (maybe someone out there has a better one)

80 gig windows primary partition

292.5gig storage primary partition

EXTENDED PARTITION
{
2 gig swap logical partition
500 meg boot (just for safety) logical partition
5 gig home logical partition
20 gig root logical partition
}

then mount the storage partition as /music or /personaldata (or whatever)

---

### Post by blackbinary on 2008-02-18
Alright, well im up and running, just about done the install.

I ended up partitioning like this:

80GB HDD:

WinXP install and documents etc. (50GB)
NTFS Storage (30GB) ~ Figure I'll use this for files I need specifically just for XP. Not shared with ubuntu

320GB HDD:

NTFS Storage (150GB) ~ shared storage for linux and xp
Ubuntu (170GB) ~ Includes root and home, didn't see the need to seperate them, might if I need to fresh install later.

Seems good to me, i've got plenty of room for both XP files, and Ubuntu files, and a large area for common files.

---

