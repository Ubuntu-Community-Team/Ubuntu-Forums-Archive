---
title: "How to boot from CD-ROM"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by topwave on 2007-05-16
**** Hi Everyone : After going into f1 (setup ) it makes you boot up from floppy disk & windows .
I need step by step in the setup on this old computers (bios ) 
I am working with 4 computers each one different . otherwords i need help in installing ubuntu,kubuntu  or  xubuntu . ALL computers have floppy disk & only cd-rom . I tried several different methods of configeration 
of the setup(f1 ) . I donot have the real UBUNTU ,Xubuntu ,etc CD  . I tried several different downloads from the computers . after the download most asked for a cd-burner ,no cd - burner . So i asked several others for help .I was able to get ububtu on a flash drive with some help from a nearby office in my building 
withdownloaded intraburner software  & cd & dvd burner burned it onto a cd. What to I need to do is this going to work . I just tested it computer machine number 3 booted up(Floppy disk boot ) in windows 2000 went into explorer & ubuntu was ready to set up . (i took the cd out )What to i do next ? 
On Computer 1 the machine will not deal with Ubuntu  from explorer/ windows98 or trying to boot from f1 setup changing the boot file . Putting the cd-rom first on the list it still doesnot work . I need help and admit it
 I will get to master this at a later date .I need to learn Linux.  Also still waiting to get my Live real cd in the future sometime.



                            SUCCESS  TO  ALL

---

### Post by lazyart on 2007-05-16
Wow.

Old computer (you didnt say how old) would likely want Xubuntu.  In explorer when you go to the CD rom drive does it show many files/folders or just one .iso file?

Understand also that installing an OS isn't really a beginner's task.

Let us know the answer to make sure the CD was burned correctly.

---

### Post by starcraft.man on 2007-05-16
I hope I'm not the only one, but your first post is really confusing... I'm also not exactly sure what you are asking for... since you didn't give us the bios maker or any idea who made the PCs I can't really give you any specific guide to BIOS changes. All you need to do to get Ubuntu installed is to burn it (like you did... I think) and then change your BIOS to boot from CD (usually when you go into the BIOS menu you will either have the option to change the boot order in most newer BIOS or some older ones, like mine simply give you the option for a one time boot to a cd when you select that option), then reboot into it. Your BIOS should load the CD instead of your windows OS, thus getting you to the installer. I'm not quite sure what you were trying to do in windows 2000 or 98... you can't install either the live or alternate from within windows.

[Here]("http://www.psychocats.net/ubuntu/installing") is a guide to installing with the Live CD, I'm guessing its what you have... its about the same for any version your using..

If when you change the boot order (I think thats what you were saying at end) and it failed to boot to the CD, then you either have a defective CD (possible, follow [this guide]("https://help.ubuntu.com/community/BurningIsoHowto") to check its burned well) or there is a problem with that machine (i.e., CD drive issue, bios corruption, can be lots of things...) If its a problem with the machine then you will have to try and find the issue yourself, there are any number of things that can go wrong with an old pc...

Oh and one last note, since these machines are that old... its advisable that you use [Xubuntu]("http://www.xubuntu.org/") on them. I assume (since you didn't provide specs) that they might not be able to run KDE or Ubuntu.

---

### Post by topwave on 2007-05-16
STARCRAFT.MAN  

The computers are hp pavilion 6635 ,around 1998 ( pent 2,533, hardrive-10 gb ) computer 1 & 2 ,128 mb.win98 computer#2,win2000
computer 3 ,192 mb ,win 2000, /computer 4 ,320 mb with cr-rom & cd burner that doesnot work ,30 gb-hardrive ,windows xp  .  

On the cd disk I have lots of files (ubuntu ,6.10 (georgia tech. ) .

Now at another computer(no.5 ) in a different office  location .(this no.5 has a cd-rw/dvd-rw burner) I cannot mess or destroy there files . Now i DOWNLOADED ubuntu & intra recorder (burned those files to a cd disk. 
I will burn xubuntu very shorty .Must download it first .to a cd disk (with intra recorder )  

Now the other day (about 1 week ago ) I downloaded ubuntu (6.10 ) onto a flash drive from certain disktop  different computer let's say computer no.85 with no cd burner . Took it to a different Computer (no. 227 ) at a different office with a cd burner with intra burner (burned the ubuntu to a cd disk ). 

Need help on booting from cd-rom also ?      






                            Success

---

### Post by wgn on 2007-05-16
This may help if you can't boot from your CD drive.

[http://ubuntuforums.org/showthread.php?t=411189](http://ubuntuforums.org/showthread.php?t=411189)

---

### Post by topwave on 2007-05-16
I just downloaded xubuntu onto the desktop of another computer (only save mode ) with cd burner with intra recorder ,what next ?  / burn it to a disk . Then take to my old computers . Or put it on a flash drive what's the deal . 

I Need help . All this info about smart manager is (floppy disk ) very foreign .  









                                                         Topwave

---

### Post by lazyart on 2007-05-16
There are two ways to do this.  Only one is right.

The .iso is a file containing a CD-image.

If you burn the image, you are doing it right and the CD when finished will have a lot of files and folders on it.
If you burn the file, you are doing it wrong and when finished the CD will have only one file on it.

I'm not familiar with intrarecorder so you'll have to find out the proper way to do it.

---

### Post by Terl on 2007-05-16
> **topwave said:**
> I just downloaded xubuntu onto the desktop of another computer (only save mode ) with cd burner with intra recorder ,what next ?  / burn it to a disk . Then take to my old computers . Or put it on a flash drive what's the deal .                                                         

I Need help . All this info about smart manager is (floppy disk ) very foreign .  
 Topwave

Have you read any of the guides the other posters have referred you to?  This sounds like a very ambitious project for someone on his first foray into linux.  I would try one machine first.  I would also take the time to read other resources provided to me.  Sorry if I sound rude, but moving to a new operating system will take some time to learn and will require study.

---

### Post by richg on 2007-05-16
> **wgn said:**
> This may help if you can't boot from your CD drive.

[http://ubuntuforums.org/showthread.php?t=411189](http://ubuntuforums.org/showthread.php?t=411189)

Forgive me for jumping in to this thread but I have been trying to do this with a linspire 5.1.427 desktop computer with two cd readers. My linspire cd is seen if I put it in either reader. Ubuntu is not. The same Ubuntu cd is seen in another pc and laptop. I did an installation in another desktop. Nice stuff.
I followed the link and got to 
SmartBootManagerHowto

Step 4. Then use rawrite command: rawrite -f sbm.bin (rawwritewin.exe sbm.bin)

There I was lost. I did download rawwrite.
Any suggestions?
Thanks in advance.

Richard Gagnon

I forgot to mention, I have drive trays in my computer and put in the 98 hd to download rawwrite and I unzipped it.
That is so bizare to have to use windows. I almost forgot how to download and unzip stuff.
I then put in a third hd with a hd that used to have 98.

Rich

---

### Post by topwave on 2007-05-16
I finally got to boot from the cd-rom ,What the deal still a problem > 
At first the xubuntu starter page popped up . Saying Start or install xubuntu ,plus a total of  6 lines of other info . at the bottom of the page f1 for help,f2,f3,f4,f5, & f6  . I went with start or install xububtu . THEN for one minute the screen went black with a statement saying : 
/bin/sh:can't access tty; job control turned off  
 (initramfs ) 


  I need help What the deal

---

### Post by topwave on 2007-05-16
ANYBODY out there I need help .

---

