---
title: "Dual booting (Two Harddrives)"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by r0tc0d on 2007-08-23
I have two hard drives and I want to set it up so that XP is on my main hard drive and Ubuntu is on my second.. I have no clue how I would go about this.. can i? Is there a way for it to say which OS or Hard drive I would want to load with two different hard drives in??

Halp :)

---

### Post by wolfen69 on 2007-08-23
just make sure to have one hard drive unplugged while installing the other. then you can quickboot into either OS upon reboot. (F12 or similar upon reboot) or go into bios to pick drive. you can set which hard drive is to boot first(default) in BIOS.

---

### Post by r0tc0d on 2007-08-23
I heard there was a way or a program that would actually allow it to just say "windows XP" and "Ubuntu" just like if I was using one hard drive with grub or something.

---

### Post by Terl on 2007-08-23
I started with two drives also.  I have windows on the main drive and then Ubuntu on the second.  It is very easy to do.  Ubuntu installed the bootloader on the main drive and when the pc starts up you get presented with a menu asking what you want to use, Linux or windows.  Works like a charm.

---

### Post by Terl on 2007-08-23
> **r0tc0d said:**
> I heard there was a way or a program that would actually allow it to just say "windows XP" and "Ubuntu" just like if I was using one hard drive with grub or something.

Yes, the Grub bootloader will be installed (as long as you allow it).  By default it will install on the MBR of your main drive.  Remember, windows likes to be first, so leave it on the drive windows calls "C".

> just make sure to have one hard drive unplugged while installing the other. then you can quickboot into either OS upon reboot. (F12 or similar upon reboot) or go into bios to pick drive. you can set which hard drive is to boot first(default) in BIOS.

Wolfen:  why do it this way when the boot loader can handle this function.  Having to go into the BIOS each time would be annoying to me.  Heck, I have had grub set up to boot windows or any one of 4 linux distros.

---

### Post by r0tc0d on 2007-08-23
Okay so I am guessing all I have to do is.. unplug my main hard drive, plug in the one i will be using for ubuntu, install ubuntu on it.. then when i reboot just plug in the windows hard drive too and grub will be installed and recognize that there is two?

---

### Post by Terl on 2007-08-23
> **r0tc0d said:**
> Okay so I am guessing all I have to do is.. unplug my main hard drive, plug in the one i will be using for ubuntu, install ubuntu on it.. then when i reboot just plug in the windows hard drive too and grub will be installed and recognize that there is two?

That is a more convoluted way of doing this.  Example:  I have 2 sata drives.  Windows is on the 120GIG drive.  I then put in the Ubuntu disk and when I clicked install, I selected the 80GIG SATA drive.  Ubuntu loaded on the drive and installed Grub on the MBR of the 120GIG windows drive.  When I reboot the grub loader comes up with a menu.  Make your choice and off you go.  There is no reason to unplug/plug drives and play with bios each time.

What are your pc specs?  Are your drives both SATA?  Are they both internal?  We can get you up and running in no time :)

---

### Post by wolfen69 on 2007-08-23
by not unplugging drives during install, grub may overwrite the MBR on xp. which would require fixing xp's mbr, should you decide to get rid of ubuntu. why make it more difficult? ive done my method on several pc's, and works great. i'd rather not have either OS fool around with anything related to boot up. it's just as easy to pick which OS with my method without fooling with grub.

---

### Post by Terl on 2007-08-23
> **wolfen69 said:**
> by not unplugging drives during install, grub may overwrite the MBR on xp. which would require fixing xp's mbr, should you decide to get rid of ubuntu. why make it more difficult? ive done my method on several pc's, and works great. i'd rather not have either OS fool around with anything related to boot up. it's just as easy to pick which OS with my method without fooling with grub.

All you do to fix the boot record is start with your windows cd and go to recovery console.  Type FIXMBR and all is done.  

Your way works, I have never had a problem with Grub or even Lilo for that matter.

---

### Post by wolfen69 on 2007-08-23
grub is fine if you're dual booting on the same hard drive, but serves no useful purpose if OS's are on seperate drives.

---

### Post by wolfen69 on 2007-08-23
> **Terl said:**
> All you do to fix the boot record is start with your windows cd and go to recovery console.  Type FIXMBR and all is done.  

Your way works, I have never had a problem with Grub or even Lilo for that matter.
 yes, i know how it is done. i fix pc's for a living. but if you don't believe my method is easier, fine. to each his own.

---

### Post by r0tc0d on 2007-08-23
So do I plug in my 2nd as a master or a slave?

---

### Post by Terl on 2007-08-23
> **r0tc0d said:**
> So do I plug in my 2nd as a master or a slave?

Well, there are two methods being discussed here and either one will work for you.  Which one do you want to try.  Wolfen's method is different but will make it easier for you if you do not like Ubuntu.

---

### Post by r0tc0d on 2007-08-23
No i have been dual booting ubuntu and XP for a while on a single hard drive and I like ubuntu, so your way would be much better for me.

---

### Post by Terl on 2007-08-23
What kind of drives are they, IDE, SATA, PATA?  Mine are SATA, when I got the second drive I just stuck it in the slot and plugged it in.  I just left the jumpers as they were.

You do have the option of staying with the dual boot on the main drive and just using the entire 2d drive as storage for both O/S's.  You could set the entire 2d drive as FAT32 (or even NTFS if you want to get the ntfs 3g stuff for Ubuntu or even EXT3 and get the driver for windows to read/write from that.)

What are the drive sizes?  Do you have any goals you want to achieve that might affect the partitioning?

Essenetially installing Ubuntu on the second drive would be similar to what you did in your first installs.  On the screen where you select where to install it, select the new drive (if that is where you want it) and it will put the boot loader on the windows drive for you.

(BTW, I am leaving work in a half hour so if I disappear that is why :)  )

---

### Post by r0tc0d on 2007-08-23
Well, The 2nd drive is only 30Gisg nice and small :D its IDE my main is 120Gigs and its SATA.

I will mainly be using Ubuntu and then the occasional game or two ill switch to XP

---

### Post by Terl on 2007-08-23
I have seen quite a few postings here where folks have a SATA main and an ide secondary and have difficulties with Grub when they have windows on the sata and Ubuntu on IDE.

What I would do (Lord knows I ain't perfect either - there may be another way) is partition the sata drive to have both O/S's there and use the ide drive as storage.

---

### Post by r0tc0d on 2007-08-23
Can you give me an idea on how to do so or a link to a tut?

---

### Post by Terl on 2007-08-23
The first step is planning how much space you want/need for each.  If XP is installed now how much space is being used on the drive for it?  How big is that drive?

Once you have that sorted out defrag the xp drive.  I would also go ahead and install the second drive and let windows format it as fat32.  Make windows do something :)

You need to leave enough room for xp to have its swap file space and room to grow if you are going to keep using it (you will have the extra drive for more room too).  Once you have that figured out the rest can be for ubuntu.

Do you want to install Ubuntu with a separate /home partition?  This will make it easier if you upgrade later.  This site has great tutorials:  [Psychocats]("http://www.psychocats.net/ubuntu/index.php").

I use this one a lot too:  [Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu_Feisty")

This one is good:  [Dual Boot Guide]("http://users.bigpond.net.au/hermanzone/")

And from our forums:  [Starcraft Man's Guide]("http://ubuntuforums.org/showthread.php?t=500020")

---

### Post by steve-shinn on 2007-08-23
> **wolfen69 said:**
> grub is fine if you're dual booting on the same hard drive, but serves no useful purpose if OS's are on seperate drives.

Yes it does .... it saves you messing in the bios every time you boot up !

---

### Post by sleepingdragon on 2007-08-23
I dual boot from two drives, windows on my original and ubuntu on my second. I've never had a problem letting grub or lilo handling a boot menu -where you get to choose windows or ubuntu at boot. I know both grub and lilo are not perfect, show me a boot system that is, but they're as solid as anything else I've seen.

I've installed dual boots on dozens of systems with no failure at all, either on desktop or laptop

Just my $0.02

---

### Post by r0tc0d on 2007-08-23
Thanks for the input, makes me feel a bit better about doing this..

im curious.. when I put the ubuntu CD in and reboot it will ask me which drive I want to load it up on? :\

---

### Post by wolfen69 on 2007-08-23
> **steve-shinn said:**
> Yes it does .... it saves you messing in the bios every time you boot up !

i don't have to mess with the bios at boot up. i hit F12 and select which drive to boot. it is seperate from bios, and takes all of 3 seconds.

---

### Post by ddnev45 on 2007-09-30
This seems like a good thread to post to while I continue searching the forums.

I'm coming over from Red Hat to give Ubuntu a try (really like it on my laptop). On my desktop I've always dual booted with two hard drives. Windows XP is on the first hard drive and Linux on the second. My preference has always been to use the Windows boot loader and not grub.

My question is: when I get to the install grub part of Ubuntu (7.04) what is the proper syntax to use to install grub on the Ubuntu hard drive? The default is hd0. I've tried a couple options. When I tried hd1 and hd(1,0) I actually got to the grub menu (using the BIOS) but get:
Error 17, cannot mount selected partition.

During the install, the Windows hard drive is hda, and the second hard drive is hdc (the CDROM is hdb, same as Red Hat).

Do I need to be using the alternate and not the live CD? Drives are configured as Primary and Secondary Masters, does the second drive **need** to be a slave for Ubuntu to dual boot?

Thanks, in advance; my search continues.

---

### Post by Wynne G Oldman on 2007-09-30
> **wolfen69 said:**
> i don't have to mess with the bios at boot up. i hit F12 and select which drive to boot. it is seperate from bios, and takes all of 3 seconds.I think your method of booting is best. Before I dumped windows completely, this is how I did it. It's great if you're trying different versions of Linux, also, it's much better for backing up drives independently of each other, e.g. if you mess up your Linux drive whilst experimenting, you can simply restore it without effecting the operating system on the other drive. Also, if you decide that Linux isn't for you, your previous operating system is totally unaffected, and will boot just as before.

---

### Post by Therion on 2007-10-01
Total linux noob here with related question...

I have Windows installed on my my primary hard drive, a 200GB, **SATA**.  Ubuntu is installed on my secondary, 120 GB, **PATA** hard drive.  To install Ubuntu, I physically disconnected my primary (SATA) hard drive and configured the secondary (PATA) drive as the Master.  All is well and Ubuntu is running fine.  

However, if I re-connect the SATA drive, Windows boots automatically.  No boot menu, just straight to Windows.  

Am I understand this correctly... That I could re-connect the Windows drive and then simply use the F12 key during startup to get a boot-menu that would allow me choose which OS/hard drive I want to boot from?  Because if that's the case... that would be awesome.

---

### Post by ddnev45 on 2007-10-01
The key to change is boot order is specific to each computer. Mine is F11; there should be a message on the screen when you start your computer. Something like: F2 to enter setup F11 to change boot order.

---

### Post by Kymus on 2007-10-17
From what I understand, this "F12" option is more what I am looking for.

I have 3 internal SATA drives and 1 external USB drive. I'm looking to keep my windows partition on one drive, and use a different drive for Ubuntu (while keeping the other two drives for backups). Although I'd like to ideally make Ubuntu my primary OS while just keeping windows around in case I ever need it; so when booting, I'd like to be able to go to Ubuntu straight away and only worry about pushing a button or using a menu when I want to load windows.

---

