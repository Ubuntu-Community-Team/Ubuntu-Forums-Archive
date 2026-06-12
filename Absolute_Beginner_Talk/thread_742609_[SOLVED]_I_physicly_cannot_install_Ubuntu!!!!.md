---
title: "[SOLVED] I physicly cannot install Ubuntu!!!!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-01
I simply cannot install Ubuntu on my machine...period.  I have an old hard drive that had Acronis on it.  I could not get it out.  Any attempt to acess the drive would cause the machine to crash.  It took over and would NOT ALLOW ANYTHING unill it rebuilt itself.  I finally had to resort to a disc eraser.  I now have a partitioned NTFC formatted drive in my machine ready to accept Ubuntu.

Problem is there is no way to acess Ubuntu to install it.  The initial loader is not there on the hard drive any more.  So a solo drive install will just not work.  Windows will not accept an image so I cannot access the disc to start an install from Windows.

I realize that I could run out and buy a new drive.  But this would kind of defeat the purpose of this install.  I have a perfectly good 80Gb IDE drive.  I just cannot find a work around to get it into my box.  Any help would be appreciated.

I'm really getting frustrated with Windows and it's me..me..me attitude.  I had Ubuntu loaded in a virtual box.  I liked it enough to want to try it for real.  I just cannot get from here to there.  My last resort is to buy another drive and start over.  Unless someone knows how to put the initial loader back onto the drive.  Thanks for letting me rant.  Any help would be appreciated.

Mark Shuman

PS: I want to dual boot with 2 drives.

---

### Post by Therion on 2008-04-01
I don't understand why you don't just download a Ubuntu [LiveCD](http://www.ubuntu.com/GetUbuntu/download).  

You can boot from the LiveCD - all by itself - and then do a full install to the hard drive from the same CD whenever you're ready.

---

### Post by NightwishFan on 2008-04-01
gparted?

---

### Post by jISh on 2008-04-01
I was thinking, since when does loading an installer from a CD have anything to do with the hard drive? :O

---

### Post by twright on 2008-04-01
were you trying to use wubi/8.04?

if so just use a live CD, ubuntu will install it's own boot menu

---

### Post by phread59 on 2008-04-01
I forgot the exact message, it's something like wdloader missing.  There is a small program apperantly on the hard drive to tell the machine to go to the cd drive and open thefile and begin installing.  There is nothing at all on the drive.

Can I load the op system from a live cd?  Where do I get one?  I'm going to look around and see if I can download it.  If I could get Windows to open it I would just have windows stick it on the drive.

Any suggestions on how to load the op system from a live cd or session.

Mark Shuman

---

### Post by Tatty on 2008-04-01
Get ubunu here: [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

Burn it to a cd (dont burn it as a data cd, you need to select "burn cd image" or something similar from your burning software).

Put it in your machine, reboot.  When it boots it should run the live CD.  assuming there are no errors, it shoudl load to a desktop.  On the desktop you will see an icon labeled "install" click that to begin the install.

---

### Post by Duck2006 on 2008-04-01
This is a guide for dual booting ubuntu and windoze.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Doorslammer on 2008-04-01
Set BIOS to Boot from CDROM  first ? 
little lost with  his post 
but I think he needs to change his bios setting  so the cd will boot 
I could be wrong & read the post all wrong LOL

---

### Post by phread59 on 2008-04-01
Ok a little more information.  Everytime I try to install from a live cd or the dvd the system crashes.  I go through BIOS and it just stops loading anything.  It sits there with a blinking cursor.  You can do nothing.  Unhook the IDE drive, restart and Windows starts up from the SATA drive normally.  Any attempt to run the live cd fails completely.  Windows grumbles and says it cannot open it cause it doesn't know what program formatted(??) it.  I got it onto my desctop in en Explorer file and tried to open it.  It flashed a white screen and went back to the stupid Windows box "do you want to open, yada yada"

Even trying to run the live cd dorked the ide drive.  Any attempt to load Ubuntu onto this drive or run it while the drive is hooked up dorks it.  I have to erase it or it crashes the whole machine.  It boots past post and then just shows a blinking cursor.  No keyboard keys are active except the enter key and control alt & delete.

Now I used the disc I'm trying with to load a vitrual box and ran Ubuntu inside the virtual box just fine.  So the disc works.  It is just killing this drive somehow.  I can assign it and format it in Windows.  So I believe it reads and writes.

I have used the Bios to boot from CD and it won't install it onto the drive.  I am beginning to believe the drive is toast.  Although Windows likes it just fine.

I'm about at my wits end here.  I am somewhat computer literate.  I am ok with these things.  I can do most things I want to without any help.  I'm just at a loss here.  I do have another drive I may try.  But I was saving that for building a server.

Any help would be appreciated.

Mark Shuman

---

### Post by Duck2006 on 2008-04-01
Is the IDE drive on the same line as the DVD?
If so have you set the jumpers up right, ie master/slave?

---

### Post by ugm6hr on 2008-04-01
> **phread59 said:**
> Everytime I try to install from a live cd or the dvd the system crashes.  I go through BIOS and it just stops loading anything.  It sits there with a blinking cursor.  You can do nothing.  Unhook the IDE drive, restart and Windows starts up from the SATA drive normally.  Any attempt to run the live cd fails completely.  Windows grumbles and says it cannot open it cause it doesn't know what program formatted(??) it.  I got it onto my desctop in en Explorer file and tried to open it.  It flashed a white screen and went back to the stupid Windows box "do you want to open, yada yada"

Even trying to run the live cd dorked the ide drive.  Any attempt to load Ubuntu onto this drive or run it while the drive is hooked up dorks it.  I have to erase it or it crashes the whole machine.  It boots past post and then just shows a blinking cursor.  No keyboard keys are active except the enter key and control alt & delete.

I have used the Bios to boot from CD and it won't install it onto the drive.  I am beginning to believe the drive is toast.  Although Windows likes it just fine.

This is confusing.

Can you boot the LiveCD or not?  If not - try the AlternateCD.

A hard drive error would have nothing to do with booting the LiveCD, only installing on to the HD.

---

### Post by phread59 on 2008-04-01
Therion, that is exactly what I am trying to do.  I have the live cd.  It just will not work.  It will not even run on the machine.  Windows XP PRO 64 bit is what is on the machine right now.  I am beginning to wonder if that isn't part of the problem.

I'm really gettin tired and am gonna turn in for the night.  Thanks for the help.

Mark Shuman

---

### Post by fmartinez on 2008-04-01
ugm6hr has the right idea. It maybe a memory issue on your pc. The alternative CD is a text based installer. It maybe more tollerable to your older system. 
GOOD LUCK!

---

### Post by phread59 on 2008-04-01
Duck, yes the jumpers are right, checked in BIOS and verified it is master in the primary IDE channel.

UGM6HR, no the live CD will not load or run.  Windows is throwing a hissy.  It insists the disc is an image and doesn't know who created it.  And it refuses to deal with it.  

I have tried 32 bit and 64 bit versions and nothing at all works.  Windows is just not allowing any other operationg system on board.  I may have to spend for another hard drive.  Unhook all the drives and put a new one in and do a fresh install.

Mark Shuman

---

### Post by Doorslammer on 2008-04-01
yes the alt cd is what he needs.

---

### Post by Mogurijin on 2008-04-01
If he is running "Windows XP Pro 64" his machine can't be to old since it is 64-bit compatible. So the machine works and boots perfectly without the IDE drive? Can you get into BIOS and boot to the cd without the IDE drive in? If you're having issues with booting to BIOS with only the IDE drive, you could try to flash BIOS. Also, you said Windows plays fine with the drive. I'm guessing you've tried formating the drive through Windows? On a last note, you could try to take out your SATA drive and try to install Windows on the IDE and then try the live cd again. This might make the drive play nicer ;).

---

### Post by phread59 on 2008-04-01
FM this is a brand new machine.  It is only a month old.  I built it myself.  it has an Intell 6550,4GB 64bit memory,8600GT card,Asus P5N-E board,Windows XP Pro 64 bit.  It is not an old hardware issue.

Mark Shuman

---

### Post by jesusfreak107 on 2008-04-01
> **phread59 said:**
> Therion, that is exactly what I am trying to do.  I have the live cd.  It just will not work.  It will not even run on the machine.  Windows XP PRO 64 bit is what is on the machine right now.  I am beginning to wonder if that isn't part of the problem.

I'm really gettin tired and am gonna turn in for the night.  Thanks for the help.

Mark Shuman
Okay, it looks like you have panicked.  therefore, the first thing you need to do is calm down, and restart from the beginning.  You said the LiveCD would not work, and the computer said that it was the HDD's fault?  Try unplugging both of the HDDs, and booting off of the LiveCD, and see it that works.  

Also, another thing. Can you get to the menu that asks how you want to boot?  (normaly, alternate, text, HDD, etc)  If so, and the problem occurs after that, then, when you are on the menu, press F6, I think, or whatever you need to do to change the boot line.  then add: >  boot:linux pci:nosort  (and maybe "text" at the end).  If that does not work, or does not apply, it appears that you have burned it incorrectly.  Try googling and downloading an opensource/freeware application from a site such as Download.com that is made for specifically burning "ISO" files.  Download and burn the ISO file you get from Ubuntu.com, and try it again.

---

### Post by jesusfreak107 on 2008-04-01
> **phread59 said:**
> FM this is a brand new machine.  It is only a month old.  I built it myself.  it has an Intell 6550,4GB 64bit memory,8600GT card,Asus P5N-E board,Windows XP Pro 64 bit.  It is not an old hardware issue.

Mark Shuman
If you do not have any valuable info, download Parted Magic LiveCD from Download.com, and, with the ISO software I mentioned in my previous post, burn it, boot off of it, and do a plain, aggressive, EXT3 format on BOTH of the drives, and disregard any warnings.  Oh, and don't forget a SWAP partition.  say, 1GB.  then, retry your Ubuntu CD

---

### Post by phread59 on 2008-04-01
Mojurin, XP is on a Stata drive.  I'm trying to install onto a salvaged IDE drive.

Jusesfreak'I'm not panicking, just getting frustrated.  After fixing cars for 26 years freaking out over a technical problem is not an option.  Do it every day.  Tomorrow I will try the no drive thing and verify that the disc will load and run.

No I can't even get that far.  Like I said I ran a virtual box previously.  I sucessfully loaded Ubuntu and had it installed and running.  Wanted to do a permanent install.  It's just beating me up.  BTW the disc I used for the virtual box is the same one I'm using now.

Maybe because it's an image it won't load right.  I beleve an iso file may be the key.  I'm starting to burn out.  I'm heading to the barn.  I'll try the download and the no drive trick tomorrow.

Good night and thank you all for your kind help.  You have no idea how good this feels, with this amount of help.

Mark Shuman

---

### Post by Tatty on 2008-04-01
> **phread59 said:**
> 
Maybe because it's an image it won't load right.  I beleve an iso file may be the key.  I'm starting to burn out.  I'm heading to the barn.  I'll try the download and the no drive trick tomorrow.

Just to clear up a few things...

1. An "image file" is basically all the data from an entire cd which has been fit into one big file.  When you burned it to CD, it ceased to be an image file and instead created an exact copy of a ubuntu install cd.

If you look at the contents of the CD you will see lots of folders and files, which are your installers for Ubuntu.

2. Installing Ubuntu has nothing to do with windows (excluding wubi installs, but ignore that for now).  Windows should not be loaded and will not have any ability to control the ubuntu installation.

3. Some of your posts are a little confusing... It would really help if you could provide some more detail about exactly where it fails to load.  When you reboot, what exactly DO you see, and where does it fail?  if you could be as descriptive as possible, that will help.

---

### Post by rovr138 on 2008-04-02
> the disc I used for the virtual box is the same one I'm using now.

> Maybe because it's an image it won't load right. I beleve an iso file may be the key

If you used a CD to install to your Virtual Machine. You shouldn't have a problem using it to install to the Hard Drive. 

If you used an image (*.iso) to install in the Virtual Machine and then burnt it to install on the Hard drive. It could be a problem with how you burnt it. 

If you burnt it after the Virtual Machine install. You might have burnt it as a Data CD. 

In Windows, you could try [_ImgBurn_]("http://imgburn.com") to [_burn the image onto the CD_]("http://www.imgburn.com/index.php?act=guides")


If the CD is burnt ok. Try and verify the Boot order again. CD before the Hard Drive...

You could check with your virtual machine if the CD is ok. If it doesn't have any errors. (Boot from CD drive, on the Ubuntu menu that appears, select the option to check the CD for errors)

---

### Post by ugm6hr on 2008-04-02
> **phread59 said:**
> UGM6HR, no the live CD will not load or run.  Windows is throwing a hissy.  It insists the disc is an image and doesn't know who created it.  And it refuses to deal with it.  


Again, I think you have the wrong idea.

Windows does not need to know anything about the disc.  It should run from boot-up, not from within Windows.

However, the fact that you can't browse the files on the CD from Windows tells me there is a problem with the CD.

How are you burning them?  This explains [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Therion on 2008-04-02
Okay, ummmm... no offense intended here, but posts like this one:
> **phread59 said:**
> ... the live CD will not load or run.  Windows is throwing a hissy.  It insists the disc is an image and doesn't know who created it.  And it refuses to deal with it.  

I have tried 32 bit and 64 bit versions and nothing at all works.  Windows is just not allowing any other operationg system on board...
confuse the daylights out of me.  

You do understand you put the Ubuntu LiveCD in the optical drive and then *reboot* your PC with the CD in the drive, correct?  It's a bootable CD, that's the whole point -- to bypass the Windows startup process.  You do not use Windows in any capacity, or even boot INTO Windows to use the LiveCD.  If this is what you're doing (booting your PC with the LiveCD in the optical drive), how is it Windows is "throwing a hissy"??  This indicates you are in a Windows environment at some point and trying to do... something... with the LiveCD.  This is not correct.

If you're not booting into Ubuntu using the LiveCD - and we assume the LiveCD is:  a) a good burn and b) a proper .iso file (as you say it is) - then it seems to me that logic dictates that one of two things simply *must* be happening:  

1.  The LiveCD is not in the drive during startup 

or 

2. The optical drive has not been set as the first device in the bootable-device chain.  Startup is therefore bypassing (if you will) the optical drive and looking to the next device in the boot-chain which would be, logically speaking, the hard drive, which obviously is no good in this situation.

---

### Post by phread59 on 2008-04-02
OK guys, I'm back again.  I'm not as brain dead as last night.  I put my copy of the CD in with no drives hooked up and Unbuntu won't load.  Error message "NTLDR is missing" comes up.  My IDE drive when it's giving problems will lock out the system.  I only get a blinking curser.

I used HDDerase again.  I noticed a line in the DOS program telling me the drive is locked.  I erased it again.  On the reboot with the Windows drive now attached as well as the erased IDE drive  I got the "NTLDR missing" prompt again.  Robooted and went into BIOS again and reset back to original values.  Now we are booting into Windows and all is well.  This leads me to believe NTLDR is some kind of a boot loader on the bios.

Therion, I tried your no drive trick.  No soap, so I went into the previous posts and found a link to the live CD.  It's downloading right now.  The number of choices is significantly higher than I saw when I downloaded my disc before.  This seems to confirm I do not have the live CD.  In all cases I went from the download right to the disc.  It appears my other discs are not live CD's.  I went directly to the home page and downloaded them there.  Tatty, you appear correct.  Windows refuses to open the image file because it does not know what created it.  If it would have opened it I could have found the EXEC file and kick started it myself.

I'm gonna try this.  I'm going to try Jesusfreak's advice.  I'm going to initialize the drive but not format it.  I'm going to get a copy of partition majic and partition it and format it directly to EXT3.  Then reboot with the live CD and try to install with the Windows drive disconnected.  If all goes well I have printed some threads on dual booting.  I have the instructions for setting up Grub and map the drives.  We'll go on from there.  I'll report back later.

I at this time want to thank you all for hanging in there with me through this.  At times I have been very frustrated.  It has been many late nights.  And a whole weekend last weekend failing.  I'm just to ornery to give up.  Heck running 400-600 line programs on a card reader was easier than this.  With your help I'll get there.  Thank you all very much.

Mark Shuman

---

### Post by philinux on 2008-04-02
Totally confused.

you burn the iso as an image to a cdr or cdrw

You set your bios to boot from cdrom/dvd first.

Reboot with the live cd in the cdrom/dvd drive.

No windows involvement at all. Period.

---

### Post by amazingtaters on 2008-04-02
> **phread59 said:**
> OK guys, I'm back again.  I'm not as brain dead as last night.  I put my copy of the CD in with no drives hooked up and Unbuntu won't load.  Error message "NTLDR is missing" comes up.  My IDE drive when it's giving problems will lock out the system.  I only get a blinking curser.

I used HDDerase again.  I noticed a line in the DOS program telling me the drive is locked.  I erased it again.  On the reboot with the Windows drive now attached as well as the erased IDE drive  I got the "NTLDR missing" prompt again.  Robooted and went into BIOS again and reset back to original values.  Now we are booting into Windows and all is well.  This leads me to believe NTLDR is some kind of a boot loader on the bios.

Therion, I tried your no drive trick.  No soap, so I went into the previous posts and found a link to the live CD.  It's downloading right now.  The number of choices is significantly higher than I saw when I downloaded my disc before.  This seems to confirm I do not have the live CD.  In all cases I went from the download right to the disc.  It appears my other discs are not live CD's.  I went directly to the home page and downloaded them there.  Tatty, you appear correct.  Windows refuses to open the image file because it does not know what created it.  If it would have opened it I could have found the EXEC file and kick started it myself.

I'm gonna try this.  I'm going to try Jesusfreak's advice.  I'm going to initialize the drive but not format it.  I'm going to get a copy of partition majic and partition it and format it directly to EXT3.  Then reboot with the live CD and try to install with the Windows drive disconnected.  If all goes well I have printed some threads on dual booting.  I have the instructions for setting up Grub and map the drives.  We'll go on from there.  I'll report back later.

I at this time want to thank you all for hanging in there with me through this.  At times I have been very frustrated.  It has been many late nights.  And a whole weekend last weekend failing.  I'm just to ornery to give up.  Heck running 400-600 line programs on a card reader was easier than this.  With your help I'll get there.  Thank you all very much.

Mark Shuman


Okay, there's one thing in here that I kinda latched onto, and it's that you seem to thing there should be some sort of .exe file to start the Ubuntu installation. Dunno if this is true or not, but it's the impression that I got. Exe's are windows files, and aren't used in Linux. Also, when you reboot, make sure you get into your bios settings and make your optical drive your primary boot drive. This is by far the most important step in your install, because booting into the livecd is necessary to install from said cd. So really be sure that your optical drive (DVD/CD/BLU RAY/Whatever) is the first thing your computer tries to boot from.

---

### Post by phread59 on 2008-04-02
Therion, lemme se if I can clarify some.  I understand the cd has to be in the drive on a reboot. 

As to Wndows pitching a hissy.  The cd I had Windows would refuse to open.  It gave a box stating that Windows could not open it because it did not know what program made it.  I have seen this a few times before.  If Windows does not understand a file format on a disc or download ect.  It throws that message and suggests it look for a program to either open it or convert it so it can open.  Tatty's comment on having the whole program and loaders on it seems to be spot on.

I believe the disc I have begins an install but somehow bombs part way through.  It then fails and leaves a corrupted disc.  This corrupted disc then tries to boot with nothing behind it.  Hence the blinking curser.

Someone earlier in this thread mentioned I would need an ISO file.  I believe he is also right.  Before initiating this download I noticed it was an ISO file.  So I think I'm going to be ok now.

Maybe a little background on me will help.  I'm 49 and currently working at a Dodge dealer as a line technician.  I have a degree in mechanical engineering (long story on how I got here).  I started playing with computers back about 79.  First home computer was a Commodre 64.  I went from there to a 128D (which I still have and still works!) to an Atari ST and then to an Amiga 500.  About then my life took a turn for the wierd and I left comuters for a long time.  About 10 years ago Dodge started doing many things on a computer so I decided to get a PC.  Got a Packerd Bell P2 machine.  Had that for a while.  Learned how to do mechanical work on that one till lightning killed it.  Then got a custom made Socket A AMD machine.  It sits behind me now, still wotking but it's working hard to keep up.  So I built a new machine a month ago.  I really started to dig deep into Windows  saw it's limitations.  So I came here.  I want to try Linux, have for some time.  I'm not afraid of it, I can use the CLI.  Soas to why I'm here you have it in a nut shell.

Mark Shuman

---

### Post by phread59 on 2008-04-02
Amazin Gator, Yea I got you.  I have tried that.  I believe it all comes down to a disc problem.  I got it to work with an Innotec virtualbox.  But then a program went onto the CD and got what it needed.  Somehow the disc just won't boot right.  Thank you for the help.

Mark Shuman

---

### Post by Tatty on 2008-04-02
It sounds like there are a couple of concepts here which you are misunderstanding, these links should point you in the right direction...

[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso")  this page will show you how to burn a ubuntu installation CD

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")  this page will show you how to use that CD to install ubuntu as a dual-boot with windows

If you dont understand anything in those guides, or if you come across any unexpected errors then feel free to post back here.

---

### Post by ugm6hr on 2008-04-02
Please read the links provided by Tatty.

I hope they will clear up some of the clear misconceptions you have about the installation process.

Also - it is worth confirming where you have found the download for the LiveCD from.

---

### Post by Mogurijin on 2008-04-02
I'm just throwing this out there, but it looks like to me that your first disc was a data disc with the iso file on it. This is why when you try to open the file that is on the disc that Windows doesn't recognize it. You might not have software to use iso's. Your virtual machine might have recognized the iso, which is why it didn't give you any issues.

Look at the guide on burning the cd that Tatty posted, is should help clear some confusion ;).

---

### Post by phread59 on 2008-04-02
OK downloaded the live CD and burned it to a disc.  It reports in Windows as an ISO file.  Unhook all hard drives.  Set BIOS to boot from CD.  Have CD in the primary IDE CD drive.  Reboot and nothing, binking curser.  I saw a small amount of activity on the drive light as the machine was booting and the drive spun for about 20 seconds or so.  Then the drive powered down and nothing.

I opened it in windows and it allowed me to save it on my desktop.  It is marked as an Intenet Explorer file.  You click it and it asks what you want to do with it.  Save, open ect.  I ask it to open it.  It shows a white screen for a second and then drops right back to the same box.  It won't open it.

It seems I cannot get my machine to open the discs.  I'm at a loss here.  It opened the Windows file on the cd just fine when I ran the initial install of XP.  Every attempt to load the Ubuntu software with my IDE drive results in a locked drive.  I have to run HDDerase to unlock it.

We have to be missing something basic here.  I'm beginning to wonder if I need a bios upgrade.  Scratching my head here.  I used Windowsdisc burner to burn the disc.  It should not affect the file.

Not sure where to go from here.  I may have a damaged disc drive.  Not sure anymore.  I may just go out tomorrow and get another drive tomorrow and try that.  I'd hate to have to spend 100$ just to load Ubuntu.

I do have another IDE drive I was saving.  I think tomorrow I will give that one a try.  It is in the same condition.  Erased and totally blank.  I have nothing to loose.  I'm thinking maybe there is something wrong with the drive.  Oh well tomorrow is another day.  Im feeling it is either BIOS or the drive at this point.

Mark Shuman

---

### Post by Tatty on 2008-04-02
Stop.  Before you do anything else, boot into windows, and look at the contents of your ubuntu live CD.  Screenshot the contents of the CD (just the root of it will do) and post it here.

It sounds like you have not burned the CD correctly.

---

### Post by phread59 on 2008-04-02
More information.  I installed the other drive I have.  Tried to install Ubuntu with the new drive hooked up.  Failed to open and install.  However this time the drive did not lock.  Probable drive problem with the 80gb drive.  Even though the bios is set to boot from a cd it does not.  Maybe we have a nested problem here, more than 1 problem.

Windows still will not open the file.  It declares it to be a.....ISO_auto_file,695mb.  Should boot ok.  It's an auto boot program.  Gonna go back into bios and see if auto boot is on.  Getting tired again, gonna knock off for tonight.

Mark Shuman

---

### Post by phread59 on 2008-04-02
Tatty, I cannot get into the file with Windows.  It won't let me into the file.  Above post is all I can get.   Any suggestions on an alternate burn.  Maybe download it and try to get Nero to burn it instead of Windows disc burner.  Opening the disc it has it's tagged as an internet explorer file.  Wondering if this may have something to do with it.  BTW thank you very much for your help so far.

Stupid question maybe.  Should I reload Ubuntu into a virtual box and attempt to download and burn a copy from Ubuntu?  Crazy thing is I got it up and running in a virtual machine but cannot do it for real.  Crazy isn't it.

Mark Shuman

---

### Post by ugm6hr on 2008-04-02
@phread59:

Your frustration is showing through here, and it is unfortunately stopping you from achieving anything.

My suggestion: Stop with your experimentation.

Please read the links provided thoroughly here [http://ubuntuforums.org/showpost.php?p=4640127&postcount=31](http://ubuntuforums.org/showpost.php?p=4640127&postcount=31)

Then follow the instructions *exactly*.  Then report back on what happens.

---

### Post by Tatty on 2008-04-02
> **phread59 said:**
> OK downloaded the live CD and burned it to a disc.  It reports in Windows as an ISO file. 

Are you saying that you see a .iso file when you look on the cd?  If so then you have burned it incorrectly.  You need to tell your cd burning software that you are burning a cd image so it can burn it correctly.

In nero you need to burn with the option "burn image to disc"

---

### Post by Mogurijin on 2008-04-02
You can also google iso recorder. It is a power toy for Windows that allows you to burn iso files.

Here is the link:
[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

---

### Post by phread59 on 2008-04-02
OK Tatty, first point of interest.  I downloaded the files from the main page of the web site.  Windows does report the file on the disc as an image.  I reported that a while back here.  I did use it with the Innotec Virtual Box and suceeded in loading Ubuntu onto the virtual box and got it working.  I for some reason cannot use it to install Ubuntu onto my machine.  I did read through the links you pointed out.  I used instructions from there to load the virtual box.
(BTW I'm not yelling or acusing or in any way dissing you.  You have been exceptionally patient and helpful.  I'm trying to give you pertinent info.  I'm tired and may seem disrespectful, but I am trying not to be.  I'm too much of a to the point kind of guy.  I tend to say what I mean in short and hopefully simple language.  I sometimes come off in a way I'm not.  I think everyone assumes I'm angry and irratable and ranting.  I really am not.  I learned long ago fixing cars for a living that you can't fix anything if you're mad.  Just trying to give you the info you need to help me and be helpful.  And I do appreciate it with all my heart.  Bless you all)

I did however print them out now.  I have a hard copy to reference.  I'm going to do as ugm6hr suggests and get the software he reccomends and go step by step tomorrow.  I have been using Windows software here mostly.  That may be my problem, or part of it.

Only 1 dumb question.  In a pile of other threads people say to dual boot you have to map your drives.  He does not go into it.  And I believe he does not say where to put grub.  Any suggestions on these.  I printed several drive mapping schemes as a reference.  Should Grub go on the PATA or the Sata (Windows)drive?

I am running Windows on a SATA drive in channel 1.  I want to put Ubuntu on a PATA drive on the only drive on the PATA channel.  Drive is set for master and only drive, on the channel with the jumper.

Guys I'm getting too tired to go on and will only make things worse by pressing on.  I'm heading to bed.  I cannot say this enough.  But THANK YOU FELLAS, you guys are the best.

Mark Shuman

---

### Post by jesusfreak107 on 2008-04-03
> OK Tatty, first point of interest. I downloaded the files from the main page of the web site. Windows does report the file on the disc as an image
THAT is your problem!  a burned Image does not appear as an image on the CD.  imagine a .zip file.  burning an ISO file on to the CD is like extracting the contents of a .zip file on to it.  if you burned it correctly, you would see a  whole CD full of folders and files, not an "image file"  your problem is burning it.  If you have Nero, but it using the"burn as image" option.  If not, download a free image burner/ISO software.  let me check...

[This one]("http://www.download.com/Active-ISO-Burner/3000-2646_4-10602452.html?tag=lst-1") looks like it should work.  remember, "burn as an image," not "burn CD" and not as a data CD.  I would install the software, and see how it works, but I am running Ubuntu right now, and it is a WIN XP/Vista program.  however, it is still FOSS, and should suit your needs perfectly.  I have an ISO burner on my Windows installation, but I have not used it in a while (ran out of blank CDs, need to get more), and I forget what it is called.

---

### Post by ByteJuggler on 2008-04-03
> **phread59 said:**
> I forgot the exact message, it's something like wdloader missing.  Mark Shuman

No.  Go into your *BIOS*, and set the boot order so the CDROM goes first.  It's not usually the hard drive's responsibility to divert to a CDROM, usually the other way round (sometimes.)

(Consider: How would you install on a brand new blank drive with no master boot record and no operating system?  The only way is to set the machine to boot from CDROM, in the BIOS which is what you should do here.)

---

### Post by ByteJuggler on 2008-04-03
As for burning .ISO files to CD's, I use [ImgBurn]("http://www.imgburn.com/") under Windows (when I'm using Windows.)  It is easy to use.

---

### Post by tangibleorange on 2008-04-03
so can you actually boot into a CD (NOT install it)? If you can, you can use the gparted facility in the Ubuntu Live CD to delete all the existing partitions. When in the CD, type this into a terminal:

```
gksu gparted
```

you should then be able to format the partitions you need to format.

forgive me if i've misunderstood...

---

### Post by phread59 on 2008-04-03
OK fellows, update time.  I now have a good copy of the live CD.  Followed the instructions UGM6HR pointed out.  Even though the check for corruption failed I went ahead and used his software and burnt a disc.

We definately have a winner.  I booted with the CD and sucessfully ran a live session.  Used Firefox to do a quick search on hotdogs (What I had for supper,with kraut!!!!).  Used the calculator and fiddled with a few applications just to verify.  This disc seems to be just fine.

I went and unlocked and erased the old 80 GB drive again.  I had the other drive working this morning.  I decided to assign it and partition it.  After I partitioned it I downloaded the file and shut down and went to work.  It appears that with the drive partitioned on a reboot the computer decides to go to the IDE channel and boot from it.  There is no operating system there so the blinking curser deal.  I thought that if the drive was ready with a partition and formatted to ext3 it would go smoother.  I guessed wrong.

Right now the drive is installed, recognized in Bios and seen by the machine.  It has been initialized.  No partition or drive number.  I'm going to try to load Ubuntu onto it.

The tutorial pointed out has no mention of drive mapping.  Nor does it suggest where to put Grub.  It is pitched toward a single drive dual boot.  I'm kinda leery of using it.  I do have several Grub mapping setting tutorials printed.  Should I just use the suggested tutorial and fix it after the fact.  I am going to assume I want Grub on the IDE drive.  It seems to want to be the first hard drive to boot.  Just to refresh everyones memory or to tell someone new to this post.  I have XP Pro 64 bit on a SATA drive in channel1.  I want to put Ubuntu onto an IDE drive set to master.

My Bios does not allow selecting which hard drive to boot from.  It only allows a choice of CD, Floppy or hard drive.

I'm fairly tired now.  I'm going to wait and see if one of you fellows(Tatty,UGM6HR) will make a suggestion on how to proceed.  It's been too many late nights and early mornings lately.  So I'm going to head to the barn soon.

As always thank you all for the help.

Mark Shuman

Edit:  Jesusfreak you are 123.98% correct.  It appears the burners I was using did not support burning an image to a CD.  I used a program pointed out in the thread I was directed to.  Now I have a good CD.  Thanks for the info.  I have been beating my head in for a stupid thing like a corrupted image on a disc.  Lordy do I feel stupid.  So many of you told me this.  To damn tired working late on this.  Shows I have a ways to go yet.  Gotta kick this Windows mindset out the window and start doing things in accordance with Linux protocols.  I do apologize for being so damn stupid.

---

### Post by ugm6hr on 2008-04-03
This thread's long, so I'm glad you've summarised what you're trying to achieve.

Just to clarify something - is there a problem with the IDE HD?  It is generally pretty straightforward to do a hardware check (see the various manufacturer's websites, or use any of the Hard Disk Diagnostic Tools here: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/))

As for GRUB - if the IDE HD is master, and first boot device, it should automatically be labelled as hd0 by GRUB.  Luckily, the MBR (Master Boot Record) of hd0 is the default location for GRUB to be installed when using the LiveCD.  So you needn't worry about that at all.  

Also, because XP is installed on hd1, with it's own bootloader on hd1 MBR, if you ever have to remove the IDE HD, XP should automatically boot without needing to restore anything.

So - provided the HD is working OK, there should be no problem with completing this successfully.

Just one word of warning though...  If the CD check reports errors, you *may* find that the installation goes a bit haywire.  But you can't really do much harm to a blank HD anyway!

PS: It was Tatty who first directed you to aysiu's excellent Ubuntu installation tutorial - but it's nice to take credit for shoving it in front of you!

---

### Post by phread59 on 2008-04-04
UGM6HR'  I am right now typing to you from Ubuntu on my machine permanently installed.

I finally got there, with you and many more selfless people's help.

Summary of this pile of mass confusion:

Error on my part, Not understanding that you need specific software to burn an image to a disc.  In all the years I never knew of this.  I assumed the burner just made a copy of the info as it should be.  My error completely and I do apologize profusely.

Toasted hard drive.  You could assign it, partition it,format it, but not write to it.  I borrowed some disc diagnostic software.  Seems sector 0 was not able to be written to.  I believe this is the master boot section.  No wonder it was not working.  Shove other drive in and presto chango Ubuntu on the drive easy as pie.

I want to take this moment to thank all of you for being so kind and patient.  Easy to fix if only 1 problem presents itself.  Gets fun when you have nested problems.  So the free drive I was given was fried.

Now comes the long hard part.  Working with a new system.  I am so pshyced, now maybe I can get some sleep!

Mark Shuman

---

### Post by msikka on 2008-04-04
Hi guys, I am having a similar problem with my install on a new Panasonic laptop. I'm trying to install from the live CD - it will neither run the live thing nor will it install from the disc. I get into the initial grub menu, and once I pick what I want (live or install) it shows a dialog saying "Loading Kernel" and you can see the progress bar and then a black screen with a blinking cursor for ever. Now this is Hardy Heron 8.04. I have installed from this same CD on two other laptops in the last week and the install went smooth as butter. Not only that, but I've tried installing openSUSE 10.3, PCLinuxOS and Zenwalk, and all of them give me the same problem. 

Some info about the laptop: no internal CD drive, so I'm installing from an external optical drive. I have edited the boot order in the bios - oddly it shows my Sony external optical drive separately from another option - the "optical drive". The laptop has Windows XP installed on it. I have tried only keeping the boot from the Sony optical drive on the boot order and even that does not work. This has me completely baffled. I would really appreciate any help because I have saved for a long time to get this laptop knowing that I will be able to install Ubuntu on it because of the previous installs on mine and my friend's machines.

Thanks

---

### Post by Tatty on 2008-04-04
> **msikka said:**
> Hi guys, I am having a similar problem with my install on a new Panasonic laptop. I'm trying to install from the live CD - it will neither run the live thing nor will it install from the disc. I get into the initial grub menu, and once I pick what I want (live or install) it shows a dialog saying "Loading Kernel" and you can see the progress bar and then a black screen with a blinking cursor for ever. Now this is Hardy Heron 8.04. I have installed from this same CD on two other laptops in the last week and the install went smooth as butter. Not only that, but I've tried installing openSUSE 10.3, PCLinuxOS and Zenwalk, and all of them give me the same problem. 

Some info about the laptop: no internal CD drive, so I'm installing from an external optical drive. I have edited the boot order in the bios - oddly it shows my Sony external optical drive separately from another option - the "optical drive". The laptop has Windows XP installed on it. I have tried only keeping the boot from the Sony optical drive on the boot order and even that does not work. This has me completely baffled. I would really appreciate any help because I have saved for a long time to get this laptop knowing that I will be able to install Ubuntu on it because of the previous installs on mine and my friend's machines.

Thanks


Obviously 8.04 is still in beta, so there are bugs which will appear.

But it might be worth trying to install with the alternate CD.  The Live CD doesnt always work.

---

### Post by msikka on 2008-04-04
> **Tatty said:**
> Obviously 8.04 is still in beta, so there are bugs which will appear.

But it might be worth trying to install with the alternate CD.  The Live CD doesnt always work.

Hey Tatty, I would have thought so too, but for the fact that every single flavor of Linux I have tried gives me the exact same issue. The PCLinuxOS and Mandriva that I tried were distro CDs from magazines. The 8.04 that I'm trying has worked on two other laptops not only without any issues, but on one Vaio every single thing works including brightness buttons, suspend to ram and such, and with the same CD my new laptop hangs on that one place.

I'm going to try an old Fiesty Disc that I have, but I have a feeling that is going to be the same. I'll let you know. 

Thanks

---

### Post by jesusfreak107 on 2008-04-04
> **msikka said:**
> Hi guys, I am having a similar problem with my install on a new Panasonic laptop. I'm trying to install from the live CD - it will neither run the live thing nor will it install from the disc. I get into the initial grub menu, and once I pick what I want (live or install) it shows a dialog saying "Loading Kernel" and you can see the progress bar and then a black screen with a blinking cursor for ever. Now this is Hardy Heron 8.04. I have installed from this same CD on two other laptops in the last week and the install went smooth as butter. Not only that, but I've tried installing openSUSE 10.3, PCLinuxOS and Zenwalk, and all of them give me the same problem. 

Some info about the laptop: no internal CD drive, so I'm installing from an external optical drive. I have edited the boot order in the bios - oddly it shows my Sony external optical drive separately from another option - the "optical drive". The laptop has Windows XP installed on it. I have tried only keeping the boot from the Sony optical drive on the boot order and even that does not work. This has me completely baffled. I would really appreciate any help because I have saved for a long time to get this laptop knowing that I will be able to install Ubuntu on it because of the previous installs on mine and my friend's machines.

Thanks
when you have a choice of what to do, boot, boot in text, install, install in text, etc, etc, go to the first option, press F6, and add "boot:linux pci=nosort" see if that works, and report back here.  good luck!

---

### Post by msikka on 2008-04-04
> **jesusfreak107 said:**
> when you have a choice of what to do, boot, boot in text, install, install in text, etc, etc, go to the first option, press F6, and add "boot:linux pci=nosort" see if that works, and report back here.  good luck!

The boot in text is from a separate disk right? I tried the "boot:linux pci=nosort" to no avail. When you say "add", you mean: press F6, then add the "boot:linux pci=nosort" at the end of the text line that shows up at the bottom right? It ends up with something like: "some pre-existing stuff--boot:linux pci=nosort".

I'll try the text install and let you know.

Thanks

---

### Post by jesusfreak107 on 2008-04-04
ahh... almost.  No, the boot in text is not on a seperate disk.  When you stick the live CD in, you should get a menu with over 10 options on it, that does not look like GRUB.  the text is orange (on Gutsy, at least).  also, this is not right: > "some pre-existing stuff--boot:linux pci=nosort" you need a space. > "some pre-existing** stuff --boo**t:linux pci=nosort"

---

### Post by msikka on 2008-04-04
Could someone please point me to where I can get the alternative install disk for Ubuntu? I can't seem to find it even by googling?

---

### Post by msikka on 2008-04-05
> **jesusfreak107 said:**
> ahh... almost.  No, the boot in text is not on a seperate disk.  When you stick the live CD in, you should get a menu with over 10 options on it, that does not look like GRUB.  the text is orange (on Gutsy, at least).  also, this is not right:  you need a space.

Alright, here is what I get from the text mode install:

it says: boot:_
I hit enter.
Then it says casper/vmlinuz something............................................................................
                     casper/somethingrd.gz.,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,


_

and then the blinking cursor on the top left that keeps on blinking and blinking..

Oh, and the boot:linux pci=nosort does not work either.

Thanks for your quick replys guys

---

### Post by ByteJuggler on 2008-04-05
> **phread59 said:**
> Seems sector 0 was not able to be written to.  I believe this is the master boot section. 

Yes, to be exact it contains the master boot record (aka MBR, code to start the boot process) as well as the primary partition table.  If that sector doesn't work, you basically can't use the disk, at least not easily/as a boot disk.  Using Linux, you might be able to make use of the undamaged space on it in some way, however I would personally not risk that and strongly discourage it, as the drive might develop or have other problems if sector zero is already toast...

---

### Post by msikka on 2008-04-05
> **ByteJuggler said:**
> Yes, to be exact it contains the master boot record (aka MBR, code to start the boot process) as well as the primary partition table.  If that sector doesn't work, you basically can't use the disk, at least not easily/as a boot disk.  Using Linux, you might be able to make use of the undamaged space on it in some way, however I would personally not risk that and strongly discourage it, as the drive might develop or have other problems if sector zero is already toast...

So, do I have a bad hard-disk? How/ why is windows working? Should I just return the laptop?

Thanks

---

### Post by msikka on 2008-04-05
A small clarification: I do not want to keep windows on this machine, so don't feel that I need to tiptoe around the windows install. 

Thanks

---

### Post by msikka on 2008-04-05
Maybe some useful info:

I don't have the external Sony optical drive anymore (mine was borrowed from a friend), so I've switched to installing from USB thumb drive. Again, I've used this thumb drive to install 8.04 on my Sony Vaio, so I know it works. I tried booting with the following boot option:
boot: live-install acpi=off,
and I got the regular "Kernel Loading" and it shows as loading all the way 100% and then the initrd....... and vmlinuz..... messages, and then the following message:
[B][B]
[  21.849591]PNPBIOS fault.. attempting recovery
[  21.849640]PnPBIOS: Warning! Your PnPBIOS caused a fatal error. Attempting to continue
[  21.849691]PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[  21.849742]PnPBIOS: Check with your vendor for an updated BIOS
[  21.849790]PnPBIOS: get_dev_mod: unexpected status 0x37[/B][/B]

So I tried rebooting with the "pnpbios=off", and nothing, and then also with acpi=off pnpbios=off with nothing.

Also, could it be that my laptop has a slot for a modular optical drive that is empty ( I didn't order it because it was another $600, yes!) and I'm using an external optical drive? But that does not make sense. 

Another thing to ponder: I think the hard drive has a panasonic installed windows recovery partition in the hard-drive. Could that be the issue?

Thanks again.

---

### Post by ByteJuggler on 2008-04-07
Hmmm, you might actually check to see if there's an updated BIOS on Sony's site like the message suggests, and update your laptop BIOS if three is.

Also if I was you, I would try, just as a wild random guess, adding boot options

```
nolapic noapic
```

This will disable certain things which on some laptops cause trouble.  You could also possibly add 

```
vga=771
```

if you have problems seeing the bootup splash (not sure if that's part of the problem or not, but thought I'd suggest it.)

---

### Post by msikka on 2008-04-07
> **ByteJuggler said:**
> Hmmm, you might actually check to see if there's an updated BIOS on Sony's site like the message suggests, and update your laptop BIOS if three is.

Also if I was you, I would try, just as a wild random guess, adding boot options

```
nolapic noapic
```

This will disable certain things which on some laptops cause trouble.  You could also possibly add 

```
vga=771
```

if you have problems seeing the bootup splash (not sure if that's part of the problem or not, but thought I'd suggest it.)

Hey ByteJuggler, I've tried the noapic nolapic options as per the help in the boot splash, I have no problem seeing the splash. It is only after I hit enter on the boot: prompt that the system hangs. Is there an exhaustive list of boot parameters that I could try?

Thanks

---

### Post by msikka on 2008-04-07
Just talked with Dr. Durey at EmperorLinux, and they are also having issues (not exactly the same issues) with this same machine. I should have bought it from them, or done my homework really well before I bought this. Just so others are aware, this is a Panasonic CF-30 with a Core2 Duo L7500 processor. It seems that the one with the CoreDuo 1.66Ghz processor version is fine. But, they can get linux working on this for me without ACPI (hiberanate modes) working.

---

### Post by ByteJuggler on 2008-04-07
> **msikka said:**
> Just talked with Dr. Durey at EmperorLinux, and they are also having issues (not exactly the same issues) with this same machine. I should have bought it from them, or done my homework really well before I bought this. Just so others are aware, this is a Panasonic CF-30 with a Core2 Duo L7500 processor. It seems that the one with the CoreDuo 1.66Ghz processor version is fine. But, they can get linux working on this for me without ACPI (hiberanate modes) working.

Hmm, so that would imply "noacpi" might work... Perhaps you'd like to try that as well.

---

### Post by ByteJuggler on 2008-04-07
> **msikka said:**
> Hey ByteJuggler, I've tried the noapic nolapic options as per the help in the boot splash, I have no problem seeing the splash. It is only after I hit enter on the boot: prompt that the system hangs. Is there an exhaustive list of boot parameters that I could try?

Thanks

[Here']("http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt")s one place with a full list.

---

### Post by msikka on 2008-07-03
Hey ByteJuggler, thanks, I'm going to try it fresh again this weekend, with a clear and cool mind :)

Thanks

---

### Post by bondo101 on 2008-07-03
I have read  all the blog wow what a pain ! i'm running ubuntu 8.04 on and old machine that has a 266 bus speed with 1 gig of ram 2 hard drives one with xp one with linux. laptops with linux are trickey i don't think laptops have enough resourses to run linux ubuntu. I love ubuntu what an eye opener. Vista forget it. Sata drives with linux and ide drives in the same box i don't think so. Run linux by it self on its own drive it works fine. Don.t mix windows with linux they don,t play well together. Thats just my exp from the past.  The bondo man Rock on ubuntu:lolflag:

---

### Post by bobnutfield on 2008-07-04
> **bondo101 said:**
> I have read  all the blog wow what a pain ! i'm running ubuntu 8.04 on and old machine that has a 266 bus speed with 1 gig of ram 2 hard drives one with xp one with linux. laptops with linux are trickey i don't think laptops have enough resourses to run linux ubuntu. I love ubuntu what an eye opener. Vista forget it. Sata drives with linux and ide drives in the same box i don't think so. Run linux by it self on its own drive it works fine. Don.t mix windows with linux they don,t play well together. Thats just my exp from the past.  The bondo man Rock on ubuntu:lolflag:


Not sure why you had that experience, but Ubuntu (and Linux in general) will happily run on a separate IDE or SATA drive on the same computer.  My desktop has one 160GB SATA and one 40GB IDE.  I run XP and three Linux distros on the SATA and Ubuntu Hardy and Debian Etch on the IDE.  They all boot from one GRUB menu (not chainloaded.)

I have two laptops, one runs both Ubuntu Hardy and Slackware 12.1, the other runs Fedora 9 and XP.  Both run great and use ALL of the laptops features on both.  No real issues in setting up these systems, and with proper guidance, a beginner could quite easily set it up.

Sorry your previous experience led you to believe otherwise.

Bob

---

