---
title: "Dual booting throught external device"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by sdrawkcab on 2007-05-30
I successfully installed Feisty Fawn onto my external hard drive just recently. I'm having just a couple most likely easily fixable problems. 

1.) My laptop will not boot up into DOS or anything when I turn it on without the external hard drive with Ubuntu installed not plugged in. I tried going into DOS and making my laptop's primary hard drive the first thing to boot from, but no luck.

2.) I installed all of the plug ins thatwere mentioned in the sticky thread at the top of this page for media, but I still have no sound coming out of my computer.

3.) It's not really pertinent, but I can't seem to hibernate through the external drive. I tried it and my screen would not display ANYTHING. I had to take the battery out of my computer and reboot to make it work. Just wondering if that's fixable, if not, no biggy.

4.) I'm wondering what virus blocker is best to get. I know that Linux is more secure than windows of course, but I still feel like I need a form of protection.

I really appreciate any help and look forward to becoming part of the Ubuntu community. I don't have internet connection where I live (under a rock) so I may not be able to reply right away. Sorry that these problems are a little ambiguous, so just yell at me for specifics.

---

### Post by depele on 2007-05-30
Have you installed grub bootloader on the external drive or on you laptop drive?

I have installed it on the external drive. so no problems with windows. I just have to adjust the startup settings in my bios overytime I want to boot from the external drive.

Same problem here as we are talking about hibernating the Os on the external drive.
So I also request an answer on that question.

grtz..

de_pele

---

### Post by sdrawkcab on 2007-05-30
No I haven't installed that. Where can I find it if I may ask?

---

### Post by ugm6hr on 2007-05-30
> **sdrawkcab said:**
> 
1.) My laptop will not boot up into DOS or anything when I turn it on without the external hard drive with Ubuntu installed not plugged in. I tried going into DOS and making my laptop's primary hard drive the first thing to boot from, but no luck.


It sounds like you used the default settings for GRUB from the Ubuntu LiveCD.  If you install Ubuntu on an external drive, the LiveCD puts GRUB (a "program" that enables an OS to boot) on the MBR (Master Boot Record - first part of a hard drive) of hd0 (which is always your 1st internal drive).  However, it then stores menu.lst (the text file that lists where the OS are in your hard drive partitions) on the same drive as Ubuntu.

Unfortunately, that means you need to have both hd0 (internal drive) and the Ubuntu partition available to boot.  It also means it writes over any existing Bootloader on hd0 (for example Windows bootloader), so nothing will load without the external drive plugged in.

There are a number of solutions (assuming you have Windows on the internal drive).
Options:
1. Install GRUB on external drive, reinstall Windows bootloader on hd0, and have external drive as first boot device (as depele).
2. Reinstall Windows bootloader on hd0, edit boot.ini (in Windows), add GRUB4DOS in C:\ in windows, and copy menu.lst from external drive to C:\ (and have internal drive as first boot device).

I actually think that Option 2 is easier, but only because I find manually installing GRUB a bit confusing.  GRUB4DOS merely involves copying files to the correct location within Windows, which for those of us who are still more familiar with Windows, is much easier.

I am sure I have seen some good explanations of exactly how to do this, but can't find them at the moment.  All I have is my explanation here:
[http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos](http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos)

It will at least lead you to the correct place to start looking for info.

---

### Post by sdrawkcab on 2007-05-30
> **ugm6hr said:**
> It sounds like you used the default settings for GRUB from the Ubuntu LiveCD.  If you install Ubuntu on an external drive, the LiveCD puts GRUB (a "program" that enables an OS to boot) on the MBR (Master Boot Record - first part of a hard drive) of hd0 (which is always your 1st internal drive).  However, it then stores menu.lst (the text file that lists where the OS are in your hard drive partitions) on the same drive as Ubuntu.

Unfortunately, that means you need to have both hd0 (internal drive) and the Ubuntu partition available to boot.  It also means it writes over any existing Bootloader on hd0 (for example Windows bootloader), so nothing will load without the external drive plugged in.

There are a number of solutions (assuming you have Windows on the internal drive).
Options:
1. Install GRUB on external drive, reinstall Windows bootloader on hd0, and have external drive as first boot device (as depele).
2. Reinstall Windows bootloader on hd0, edit boot.ini (in Windows), add GRUB4DOS in C:\ in windows, and copy menu.lst from external drive to C:\ (and have internal drive as first boot device).

I actually think that Option 2 is easier, but only because I find manually installing GRUB a bit confusing.  GRUB4DOS merely involves copying files to the correct location within Windows, which for those of us who are still more familiar with Windows, is much easier.

I am sure I have seen some good explanations of exactly how to do this, but can't find them at the moment.  All I have is my explanation here:
[http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos](http://ubuntuforums.org/showthread.php?t=457015&highlight=grub4dos)

It will at least lead you to the correct place to start looking for info.



Hey thanks! So how long of a process do you think this would be for a first timer?

EDIT: Ok, I just rebooted and the sound problem fixed itself, so I guess you can disregard that aspect of the original post.

---

### Post by ugm6hr on 2007-05-31
> **sdrawkcab said:**
> Hey thanks! So how long of a process do you think this would be for a first timer?


Should be fairly easy, provided you are familiar with Windows.  Editing boot.ini is straightforward, provided you dont delete anything.  In order to copy menu.lst - easiest way is to do it from Windows too.  Install [http://www.fs-driver.org/](http://www.fs-driver.org/) from Windows, and just search for the file *menu.lst* in the external drive.

That way, there's no need to experiment with Ubuntu at all (except for the fun bits :).  

PS: You will need the Windows CD to do (type) *fixmbr* from the recovery console.

---

### Post by sdrawkcab on 2007-06-06
Alright, so I can't seem to find the boot.ini file anywhere on my computer. Also I found this website: [http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial]("http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial")
But I still seem to be having trouble figuring out what exactly to do. I don't know which of the Install tutorials in the link to follow or anything, and it said something about the file called "grdlr.mbr". 

Any idea on which parts of this concern me?

---

### Post by sdrawkcab on 2007-06-10
I know I know. Sorry about the double post, but the thread got pretty buried and I'm still having troubles, but with something different.

> 2. Reinstall Windows bootloader on hd0, edit boot.ini (in Windows), add GRUB4DOS in C:\ in windows, and copy menu.lst from external drive to C:\ (and have internal drive as first boot device).

I can't find any sort of tutorials whatsoever for this subject. I can't even seem to find a decent tutorial for just installing GRUB4DOS correctly. I don't know where to start for reinstalling the Windows bootloader, and I'm not sure what I should edit in the boot.ini file. 

Sorry, that's a lot of problems, and it probably seems like I didn't even try anything for myself, but trust me, I did mess around with quite a bit of stuff, so any help would be greatly appreciated :)

---

### Post by confused57 on 2007-06-10
> **sdrawkcab said:**
> I know I know. Sorry about the double post, but the thread got pretty buried and I'm still having troubles, but with something different.



I can't find any sort of tutorials whatsoever for this subject. I can't even seem to find a decent tutorial for just installing GRUB4DOS correctly. I don't know where to start for reinstalling the Windows bootloader, and I'm not sure what I should edit in the boot.ini file. 

Sorry, that's a lot of problems, and it probably seems like I didn't even try anything for myself, but trust me, I did mess around with quite a bit of stuff, so any help would be greatly appreciated :)

First you might want to install grub to the external hard drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
whatever "find /boot/grub/stage1" finds as your root partition, you would:
root (hdx,y)
setup (hdx)

If you can boot first to your external hard drive and get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd1,y) to (hd0,y), then press "b" to boot...this is temporary, but can be made permanent.

Here's a guide to restoring Window's IPL to your internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by sdrawkcab on 2007-06-12
Hey, thanks for the reply!

Alright, so is my goal here to reinstall the Windows bootloader, or should it be to install GRUB into Windows?

I see an interesting entry in that tutorial you sent in which it mentions the "Super GRUB Disc". So would that be an ideal way to fix part of my problem?

One more thing. Am I doing all of the work in Ubuntu?

---

### Post by sdrawkcab on 2007-06-19
So when I type the "fixmbr" command into the windows recovery console, it gives me a bunch of warnings about how this could be a horrible thing to do because I may not be able to access my partitions later on...Should I be worried about all this?

---

### Post by confused57 on 2007-06-19
> **sdrawkcab said:**
> So when I type the "fixmbr" command into the windows recovery console, it gives me a bunch of warnings about how this could be a horrible thing to do because I may not be able to access my partitions later on...Should I be worried about all this?
I think the warnings are normal & nothing to worry about.  Did you burn a copy of the Super Grub Disk?  You can also restore Window's IPL to the mbr with SGD.

---

### Post by sdrawkcab on 2007-06-20
Ok, well I went ahead and fixed the master boot record. 

Just one little itsy bitsy problem... Ubuntu won't boot anymore.

I fixed the problem of Windows not being able to boot without the external hard drive with Ubuntu on it, but now when I want to boot Ubuntu it just shows me a very simple error message that seems to be written in the GRUB font.

"Operating System could not be loaded". (Well, it might not be word for word)

I'm pretty sure I did everything everybody said. I put GRUB on the Ubuntu drive, and I restored the Windows IPL by booting from the recovery console and typing "fixmbr". 

P.S. What does IPL stand for?

---

### Post by confused57 on 2007-06-20
> **sdrawkcab said:**
> Ok, well I went ahead and fixed the master boot record. 

Just one little itsy bitsy problem... Ubuntu won't boot anymore.

I fixed the problem of Windows not being able to boot without the external hard drive with Ubuntu on it, but now when I want to boot Ubuntu it just shows me a very simple error message that seems to be written in the GRUB font.

"Operating System could not be loaded". (Well, it might not be word for word)

I'm pretty sure I did everything everybody said. I put GRUB on the Ubuntu drive, and I restored the Windows IPL by booting from the recovery console and typing "fixmbr". 

P.S. What does IPL stand for?

"Operating System could not be loaded" sounds like a bios error report.  Try the SGD to boot your external Ubuntu drive...
When you reinstalled grub using the live cd, did you select to install grub to (hd1)?:
```
sudo grub
find /boot/grub/stage1
root (hd1,y)
setup (hd1)
quit
```

IPL stands for Initial Program Loader, this site explains it pretty well:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by sdrawkcab on 2007-06-20
> **confused57 said:**
> "Operating System could not be loaded" sounds like a bios error report.  Try the SGD to boot your external Ubuntu drive...
When you reinstalled grub using the live cd, did you select to install grub to (hd1)?:
```
sudo grub
find /boot/grub/stage1
root (hd1,y)
setup (hd1)
quit
```

IPL stands for Initial Program Loader, this site explains it pretty well:
[http://users.bigpond.net.au/hermanzone/p6.htm](http://users.bigpond.net.au/hermanzone/p6.htm)

Yeah, I installed GRUB to (hd1) and did all of that coding you put in there. I'm pretty sure I did all of that right.

Wait, what do you mean "try the SGD"?

---

### Post by confused57 on 2007-06-20
Sorry, I thought I had given you a link for the Super Grub Disk(SGD):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You can burn a CD in Windows, then boot your computer with the SGD...then try to boot Ubuntu on your external hard drive with SGD.

---

### Post by sdrawkcab on 2007-06-20
Ok, but is that a permanent fix, or would I always have to have the SGD to boot from?

---

### Post by sdrawkcab on 2007-06-20
Is it better if I just completely reinstall Ubuntu a certain way?

---

### Post by confused57 on 2007-06-20
> **sdrawkcab said:**
> Is it better if I just completely reinstall Ubuntu a certain way?
Yes, that would probably be your best bet...what you can do is go into bios and set your external drive to boot before your internal drive, before you  install Ubuntu.  
When you get to the option to install grub, there should be an "Advanced" button that you would need to select...then you can type in "/dev/sdb", without quotes, substitute your external drive's mbr.

---

### Post by sdrawkcab on 2007-06-20
Got any good links or simple tutorials on how to uninstall ubuntu?

Oh, is there any way to save all of my programs that I downloaded for Ubuntu? I mean, I haven't got many, but still it would be nice to know for future reference.

EDIT: > ...then you can type in "/dev/sdb", without quotes, **substitute your external drive's mbr**. 

What do you mean by "substitute your external drive's mbr"?

---

### Post by sdrawkcab on 2007-07-14
I still don't get what you mean by "substitute your external drive's mbr." Is that some option that comes up after that code is typed in, or is it something I have to type in along with the code?

As for the part about saving files and such, I thought I saw an option to save stuff from previous OS when installing Ubuntu onto a friends computer. I didn't read it over too much or anything, but is this the option that I want to save my old files?

---

### Post by confused57 on 2007-07-14
> When you get to the option to install grub, there should be an "Advanced" button that you would need to select...then you can type in "/dev/sdb", without quotes, substitute your external drive's mbr.

Sorry about being a little unclear with these instructions...what I meant was your external hard drive may be recognized as something other than /dev/sdb, e.g. /dev/sdc.   However your external hard drive is recognized during the install of Ubuntu is what you would enter or by entering the command:
```
sudo fdisk -l
```
-l is a small "L"

So all you need to do to install grub to the external hard drive's mbr is to type in:
```
/dev/sdb
```

Here's an excellent site for installing Ubuntu, setting up partitions, etc:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

If you accidentally install grub to the internal hard drive's mbr, here's how to uninstall:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you need to recover files from an Ubuntu install(or Windows), you can use the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

The only way you could install over an existing Ubuntu installation and retain your data is to have a separate home partition.

---

### Post by sdrawkcab on 2007-07-14
Wow, thanks, I'm pretty sure I fully understand what I'm doing here now. 

Well, if it works out correctly and everything I'll try to remember to say so here. If not, I'll be back with another dumb question. :)

---

### Post by confused57 on 2007-07-14
> **sdrawkcab said:**
> Wow, thanks, I'm pretty sure I fully understand what I'm doing here now. 

Well, if it works out correctly and everything I'll try to remember to say so here. If not, I'll be back with another dumb question. :)
Don't hesitate to ask questions if you're unsure about something...hope you get everything working OK.

---

### Post by sdrawkcab on 2007-08-06
Ok, did all that...Twice...I got Error 17 now. So, i'm kinda worrying that I'm gonna have to do some crazy bootloader things now.

PS. Sorry it takes me so long to reply...I procrastinate a lot...

---

### Post by confused57 on 2007-08-06
> **sdrawkcab said:**
> Ok, did all that...Twice...I got Error 17 now. So, i'm kinda worrying that I'm gonna have to do some crazy bootloader things now.

PS. Sorry it takes me so long to reply...I procrastinate a lot...
Nice to meet a fellow procastinator.  Are you getting the grub boot menu when you boot first to the external hard drive, but get grub error 17 when you try to boot Ubuntu or are you not getting a grub boot menu at all?  

If you're getting a grub boot menu, highlight your Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then press "b" to boot...x means to leave this entry as it is.

---

### Post by sdrawkcab on 2007-08-06
> **confused57 said:**
> Nice to meet a fellow procastinator.  Are you getting the grub boot menu when you boot first to the external hard drive, but get grub error 17 when you try to boot Ubuntu or are you not getting a grub boot menu at all?  

If you're getting a grub boot menu, highlight your Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then press "b" to boot...x means to leave this entry as it is.

OH GLORIOUS DAY!!!!! IT WORKED! 

Thank you for all of your help. The journey of (a long fricken time) is not without it's fruits! YAAAY!

Now I get to spend a long while configuring everything.

---

### Post by confused57 on 2007-08-07
> **sdrawkcab said:**
> OH GLORIOUS DAY!!!!! IT WORKED! 

Thank you for all of your help. The journey of (a long fricken time) is not without it's fruits! YAAAY!

Now I get to spend a long while configuring everything.

Glad it worked...you can make it permanent by editing your /boot/grub/menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

You can then change your root to (hd0,x)...again, x means leave this "as is".  Also, you need to change the line beginning with #groot to (hd0,x)...leave the # in front of groot.  See this explanation:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Enjoy your Ubuntu.

---

### Post by sdrawkcab on 2007-08-08
> **confused57 said:**
> Glad it worked...you can make it permanent by editing your /boot/grub/menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

You can then change your root to (hd0,x)...again, x means leave this "as is".  Also, you need to change the line beginning with #groot to (hd0,x)...leave the # in front of groot.  See this explanation:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

Enjoy your Ubuntu.


Hey thanks! I was actually worried about that. But that solved my problem there. Well I do have a couple more problems with it actually running. Should I state them here or make new posts?

---

### Post by confused57 on 2007-08-08
> **sdrawkcab said:**
> Hey thanks! I was actually worried about that. But that solved my problem there. Well I do have a couple more problems with it actually running. Should I state them here or make new posts?

Glad to help.  Unless your problems are directly related to booting your external drive, it would be best to start a new thread(s)  with a descriptive title of the problem(s).

---

