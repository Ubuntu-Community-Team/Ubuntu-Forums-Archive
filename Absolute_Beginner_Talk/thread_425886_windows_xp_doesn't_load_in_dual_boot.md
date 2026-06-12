---
title: "windows xp doesn't load in dual boot"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by brooklyn88 on 2007-04-28
hello everyone, (long time reader first time poster). 
I just installed ubuntu feisty fawn less than an hour ago on my laptop (that I just bought). I did a dual boot since xp professional was already installed, I followed the installation instructions (and did as I saw on Alan Pope's screencast) and the install went well, I am typing this from linux.
The problem is that the xp doesn't load, it appears as an option when I start my pc but when I pick it it doesn't load, it shows the windows xp load thing for a sec and then shows the infamous blue screen that gives the error that says there is something wrong with how windows was shut down blah...blah...blah.

I can still see all my windows files through ubuntu so I know I didn't lose it. so can someone please help....much appreciated.

by the way i don't have a windows cd (bought the laptop as second hand off the net). and I need my windows stuff on it. and sorry for the long first post.

---

### Post by deadgobby on 2007-04-28
Does that screen say basically you did not start windows and bla bla bla. Just say ok and see if it will boot. Windows does not like to play nice and you need lie to it.
Gobby

---

### Post by brooklyn88 on 2007-04-28
thanks for answering so quickly (this politeness is alien to me)

when I select windows xp and click enter it takes me to the screen that says "windows did not properly shut down......" and gives me the options of starting windows in "safe mode" some other and "normal mode".
now when I click either safe mode or normal mode xp starts to load but then a blue screen pops up with some writing (for like 5 sec). Then the system restarts and comes back to the dual boot menu.

---

### Post by deadgobby on 2007-04-28
We are nice here. We do not bite and there is no stupid questions. The only stupid thing is never asking. Try all the options and see if it will boot windows. 
Gobby

---

### Post by brooklyn88 on 2007-04-28
I tried every one of them ( safe mode, safe mode with prompt, safe mode with with networking, and normal mode-last good configuration). I still end up on that blue screen (that last for 5 sec) that says I should check if I had recent hardware/software changes and that I should call my technician. that is all I could read from the five secs It's on. 

After all that it reloads back to the boot menu. ubuntu 7.04 works fine - its what I am using now- and I can even access windows xp from ubuntu but xp won't load. I need xp to load so PLEASE help.

---

### Post by msandersen on 2007-04-28
I'm not enough of a Windows expert to answer, but I think people need more information on exactly what you did when installing, in particularly partitioning. For instance, if you moved the Windows partition, particularly beyond certain limits, Windows won't boot. I forget the details, but all of the Windows boot partition must be within the first 2Gb or so on the HD. Someone with more Windows knowhow should be able to tell you, including where Windows puts its log of what went wrong. You could try finding a Windows forum.
Personally, the few times I've repartitioned, I've used Partition Magic from Windows, because I know I can trust it. There are too many potential snafus with the Linux partitioners, especially relating to the"parted" program that does the actual work. There's been a few bugs relating to partition table corruption, but that's obviously not the case here. I haven't tried Feisty, I believe they use a new partitioner, where previously they used GParted.

---

### Post by Doug11 on 2007-04-28
My guess is that if you just bought it, you had to resize your windows partition. XP does not like it when you do this (I know from past experiences). I ran into a similar problem not to long ago, except I was using Vista. I could get to the boot screen, choose MS to boot but it would hang a small ways into the bootup. The only thing that worked for my was I got an old XP disc, booted my pc from it as if I was going to do a fresh install, I let go to the point where it wanted to reformat my drives and then escaped out. Whatever files it copied during this small process let my windows boot back with no problems. The only thing I think I had to do was reinstall grub, which is very easy to do. Here is a quick and easy howto.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub)

---

### Post by bulldog on 2007-04-28
> **brooklyn88 said:**
> I tried every one of them ( safe mode, safe mode with prompt, safe mode with with networking, and normal mode-last good configuration). I still end up on that blue screen (that last for 5 sec) that says I should check if I had recent hardware/software changes and that I should call my technician. that is all I could read from the five secs It's on. 

After all that it reloads back to the boot menu. ubuntu 7.04 works fine - its what I am using now- and I can even access windows xp from ubuntu but xp won't load. I need xp to load so PLEASE help.

If you boot into ubuntu,can you open a terminal and perform the next command?
```
sudo fdisk -l
``` it's a lower case L,not a one :) 
Post the output to  the forum please.

---

### Post by brooklyn88 on 2007-04-28
this is the output os sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2609    20956761    7  HPFS/NTFS
/dev/sda2            2610        4764    17310037+  83  Linux
/dev/sda3            4765        4864      803250    5  Extended
/dev/sda5            4765        4864      803218+  82  Linux swap / Solaris

(please note I don't have an xp install disk, the image is on the computer, and I can't delete or lose my windows xp data.........thanks in advance for the help)

here are some screenshots of the drive from gparted using live cd
[IMG]http://www.geocities.com/aventuradesignz/screenshot-1.png[/IMG]

---

### Post by sailor2001 on 2007-04-28
I  think I would download and burn a SUPER GRUB disk and keep it in the files.....

---

### Post by brooklyn88 on 2007-04-28
> **sailor2001 said:**
> I  think I would download and burn a SUPER GRUB disk and keep it in the files.....

I don't know what that means (i am a complete noob, haven't had ubuntu for 24 hours yet) and I need xp to boot. it just gives me a blue screen and says drive is unmountable. I think GRUB (the boot menu right?) is working fine since I'm able to see xp and ubuntu and  am able to load into ubuntu perfectly. all the windows forums give me advice about xp/vista dual boot.

here is a video of what happens when i click windows on the boot menu.

[http://www.youtube.com/watch?v=oYFQkal4vjw](http://www.youtube.com/watch?v=oYFQkal4vjw)

---

### Post by kyphi on 2007-04-28
To get a Super Grub Boot Disk go to

[http://forjamari.linex.org/frs/?group_id=61&release_id=446](http://forjamari.linex.org/frs/?group_id=61&release_id=446)

and download the latest version.  After that double click on the dowloaded file and choose "extract".  Then burn it to a CD.   You can do all that in Ubuntu.  After that boot with the disk in the drive.

This disk will let you boot into Windows and will also fix your boot menu.

---

### Post by kyphi on 2007-04-28
You could try to edit your bootloader file (GRUB).

1. Open up the terminal (Applications -> Accessories -> Terminal)

2. Type in:

sudo gedit /boot/grub/menu.lst (then press Enter)

3.  Scroll down untill you see

# ## End Default Options ##

and add this code below it.


title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

4. Save document, exit and reboot.

---

### Post by brooklyn88 on 2007-04-29
> **kyphi said:**
> You could try to edit your bootloader file (GRUB).

1. Open up the terminal (Applications -> Accessories -> Terminal)

2. Type in:

sudo gedit /boot/grub/menu.lst (then press Enter)

3.  Scroll down untill you see

# ## End Default Options ##

and add this code below it.


title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

4. Save document, exit and reboot.

yeah its already like that, and i used grub load cd and removed grub but it still didn't load.

---

### Post by ubromtoo on 2007-04-29
Brooklynn 88 :

   I had the same problem when I first went to dual-boot.  what solved the problem

 for me was to download and install all the (Ubuntu) updates that were waiting for me.

     after that, did a restart and Windows XP worked fine.  give it a try, can't hurt anything.

---

### Post by Deguello on 2007-04-29
If you have an i386 folder in your windows files, and you are able to navigate to it in Ubuntu, try to burn those files to a disk...there is your re-install files. If you know this already...disreguard.

---

### Post by brooklyn88 on 2007-04-29
> **ubromtoo said:**
> Brooklynn 88 :

   I had the same problem when I first went to dual-boot.  what solved the problem

 for me was to download and install all the (Ubuntu) updates that were waiting for me.

     after that, did a restart and Windows XP worked fine.  give it a try, can't hurt anything.

Did that and it didnt work. I think that windows might be looking in the wrong partition. it has something to do with the way windows boots, must have messed up my windows files in using gparted during ubuntu install. anyone no any place I can get help (or r u guys windows savy too 	:shock: )

---

### Post by msandersen on 2007-04-29
Funny how no-one ever get a tripod when they get a nice new video camera, or at least manage to steady the shot for their YouTube videos.
I'm not a Windows expert, but obviously it's not a Grub problem; it's already handed over to Windows, and it seems screwed up.
Moreover, in the video the Blue Screen of Death flashes only momentarily and seems to be in German, otherwise you could Google a key phrase,especially a heading or error number.
There is one word on the video, it was cropped, but a Google for TABLE_BOOT_VOLUME comes up with the error UNMOUNTABLE TABLE_BOOT_VOLUME. That is your clue for this.
Someone posted this error message, which looks similar to the screen you got:

> A PROBLEM HAS BEEN DETECTED AND WINDOWS HAS BEEN SHUT DOWN TO PREVENT DAMAGE
TO YOUR COMPUTER.

UNMOUNTABLE TABLE_BOOT_VOLUME

IF THIS IS THE FIRST TIME YOU'VE SEEN THIS STOP ERROR SCREEN RESTART YOUR
COMPUTER. IF THIS SCREEN APPEARS AGAIN FOLLOW THESE STEPS.

CHECK TO MAKE SURE ANY NEW HARDWARE OR SOFTWARE IS PROPERLY INSTALLED. IF
THIS IS A NEW INSTALLATION ASK YOUR HARDWARE OR SOFTWARE MANUFACTURE FOR ANY
WINDOWS UPDATES YOU MIGHT NEED

IF THE PROBLEM CONTINUES DISABLE OR REMOVE ANY NEWLY INSTALLED HARDWARE OR
SOFTWARE. DISABLE BIOS MEMORY OPTIONS SUCH AS CACHING OR SHADOWING. IF YOU
NEED TO USE SAFE MODE TO REMOVE OR DISABLE COMPONENTS RESTART YOUR COMPUTER
PRESS F8 TO SELECT ADVANCED STARTUP OPTIONS, AND THEN SELECT SAFE MODE

TECHNICAL INFORMATION
***STOP: 0X00000ED ( 0X800027A0, 0XC0000032, 0X00000000, 0X00000000 )
Does that seem familiar?

Most of the Googled pages are in languages other than English, a lot of Asian ones, but try this link:
[http://wic221d.server-web.com/forum-replies-archive.cfm/648631.html](http://wic221d.server-web.com/forum-replies-archive.cfm/648631.html)

Bad news: You may need an XP disk to boot to the Recovery Console to fix this, in all likelihood.

You could look at this link:
[http://www.techsupportforum.com/microsoft-support/windows-xp-support/121170-start-up-problem.html](http://www.techsupportforum.com/microsoft-support/windows-xp-support/121170-start-up-problem.html)

the advice is:
> Check that all the Hard-drive settings are correct in the BIOS.
Make sure that the jumper settings are correct on the rear of the Hard-drive
Make sure the boot order in the BIOS is correct.
Seeing as this is on the same drive, this may not be the trouble, though.

---

### Post by msandersen on 2007-04-29
The error message doesn't show on the video, but if it's the same as above, this is the official Microsoft support page for it:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;297185](http://support.microsoft.com/default.aspx?scid=kb;en-us;297185)

Basically, if it's the "STOP 0x000000ED UNMOUNTABLE_BOOT_VOLUME" error, it can be either hardware or software: If hardware, it may be fairly easily fixed; if software, the  filesystem is damaged and needs the XP boot disk to fix it. I think you said you could access it from Ubuntu, but there may still be a crucial portion that's damaged. Maybe you know someone with XP who will loan you their disk. I don't think I'm allowed to suggest thepiratebay.org or torrentspy.com but since you legally own the computer and OS, you are entitled to obtain a n XP system disk, at least the way I look at it. 
Lesson to be learnt:  Always get the original system disks with a new or 2nd-hand computer, and do a complete backup before messing with partitioning. Always good to be wise in hindsight.

---

### Post by msandersen on 2007-04-29
I came across this post here which might be relevant:
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

You may be able to fix the NTFS partition from Linux by using the ntfsfix tool from [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)
NTFSprogs CVS snapshot:
[http://data.linux-ntfs.org/cvs-snapshots/](http://data.linux-ntfs.org/cvs-snapshots/)

---

### Post by brooklyn88 on 2007-04-29
I have tried everything that was said, ntfsfix didn't work. it said it mounted ntfs succesfully but when I restarted xp it gave me the same blue screen of death :(  . Also putting xp cd in and using the recovery didn't work, it gave me all these weird messages about not being able to find the drive etc. essentially win xp cd says it can't see win xp on my pc.

---

### Post by msandersen on 2007-04-30
Then maybe your only avenue is to recover your files from Ubuntu if System Repair from the XP disk doesn't fix it. Else a reinstall is probably the only avenue. The super grub disk can be used to reinstate Grub in that case, else there are ways to use NTLoader to boot Linux.
You could try the linux-ntfs forums, detailing the error and your attempts: [http://forum.linux-ntfs.org/](http://forum.linux-ntfs.org/)
They should know a thing or two about NTFS. Remember, error names and codes etc will help them identify the problem.

---

### Post by calgarystevens on 2007-04-30
I think this has happened to me before because my drive (ntfs) was a bit fragmented, some files were near or at the end of the drive and when moving they get a bit corrupted. Also, I think the start/finish of partitions are minutely different between the win and linux version of partitioning and sometimes that's enough to have windows say the partition is pooched. That doesn't help you, but... If you can see the ntfs partition, copy over as much as you can backup (to your linux home partition) and then burn a backup cd or cd's. Please say you have a cd burner in your new puter, or that's even worse troubles ;-) Once you are comfortable that you've backed it all up, reinstall with your restore disks, and then you can try again if you want. This time, before you re-partition, do a **thorough** defrag in windows (multiple runs would be best) and a check for disk errors, then when it's all compacted into the start of the partition go and try again. At least you know you have your backup cd's then if it doesn't work. Hope that helps.

---

### Post by bulldog on 2007-04-30
> **calgarystevens said:**
> I think this has happened to me before because my drive (ntfs) was a bit fragmented, some files were near or at the end of the drive and when moving they get a bit corrupted. Also, I think the start/finish of partitions are minutely different between the win and linux version of partitioning and sometimes that's enough to have windows say the partition is pooched. That doesn't help you, but... If you can see the ntfs partition, copy over as much as you can backup (to your linux home partition) and then burn a backup cd or cd's. Please say you have a cd burner in your new puter, or that's even worse troubles ;-) Once you are comfortable that you've backed it all up, reinstall with your restore disks, and then you can try again if you want. This time, before you re-partition, do a **thorough** defrag in windows (multiple runs would be best) and a check for disk errors, then when it's all compacted into the start of the partition go and try again. At least you know you have your backup cd's then if it doesn't work. Hope that helps.

I think only windows should be reinstalled on the same partition,ubuntu is fine after all.
If you can borrow a windows install disk you should be fine,use your own license to install though.
It's not a GRUb issue as stated before,windows is messed up some how.

---

### Post by brooklyn88 on 2007-04-30
Thank you everyone for the help, but since I already missed the deadline to get my data from the xp install I decided to clean my HD and reinstall everything from the start. I go to the threads on how to do that and do a little more research this time around :). But thanks to everyone for their help, you guys are great :biggrin:

---

### Post by msandersen on 2007-05-01
> **brooklyn88 said:**
> you guys are great :biggrin:
Yeah, we know :oops: but not great enough to fix it. :(

---

### Post by jake.keyes on 2008-05-26
I know that you've given up on this problem, but in case there are others like me who encounter similar things in the future:

I fixed this problem by going into BIOS setup and changing the hard disk behavior from Automatic/ATA to Combination.

Hope this is helpful to future searchers.

---

