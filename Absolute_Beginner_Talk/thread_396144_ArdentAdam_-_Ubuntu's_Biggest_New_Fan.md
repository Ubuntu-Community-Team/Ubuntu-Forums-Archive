---
title: "ArdentAdam - Ubuntu's Biggest New Fan"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ArdentAdam on 2007-03-29
Let me start off by saying this...I'm a long winded poster...so my posts tend to be almost like reading a novel. Just so you forum regulars are aware. :) Next, I want to say that the next version after 7.04 Feisty Fawn is released should be called ArdentAdam. :) 

I'm very new to Linux, but I love Ubuntu. Heck I could probably say that about any Linux distro...though up until now the closest I've ever been to Linux in any form would be Mac OSX...but I'm not sure how much of that is Linux (NeXT) and how much is Apple changing everything around.  

I'm 25 and actually started messing with computers 20 years ago...so I'm not entirely a computer noob, but I've never delved into Linux. Ever. I must have been scared, but now that I see it...I don't know why I ever was.
 
My first computer was a Mac Plus...then a Mac Classic...then a Mac IIsi...and then I made the conversion into PCs with Windows 3.1...then Win95, 98, ME (what a mess that one was), and then XP. I don't think I'll be going past Windows XP...now I think I can safely say I'll definitely be making a serious conversion to Linux.

At any rate...I'm impressed. Every time I've had to reinstall this system, it was due to my own stupidity and curiosity...but thats kind of necessary in order to really understand the system. Trust me...I've learned a million things over the last week and a half...I'm getting there. Have patience. :) 

Almost every problem I've had has been fixable for the most part...though not being as familiar with command lines being a Windows/Mac user...I was extremely intimidated by it at first...looking at how people try to solve problems on the internet...they don't use "ok go to this window, use that program...do this do that..." which is what I'm used to...and when they say "enter sudo gedit /dir/dir/dir/somefile and change this line to xxxx", I would look in disbelief and say "you've got to be kidding me! I HAVE to do it this way?" 

But now I understand that so much of Linux is run by these text files, that, yes, it is necessary...and its almost better that way...cause I like to tinker with my operating systems. :) Now that I've used the terminal several million times...I look at "use sudo gedit /dir/dir/dir/somefile and then change this line to that" I say "really? that's all I have to do?" And almost 80% of the time it is all I have to do. So I love that. Windows is never that simple. NEVER. 

I'm tired of Windows...and now Vista is out...and while I was a little bit interested in seeing it...I have now seen it...and I'm not impressed at all. It looks like an over-glorified version of XP...I think its actually based on an updated and improved XP/2000/2003 kernel...which means it's probably gonna work ok most of the time...but when there are problems...it'll suck trying to fix them.

I am writing this on my fiance's XP machine...but I use Ubuntu on my laptop as a dual boot with XP (which I plan sometime soon to completely phase out in favor of Ubuntu). When I wanted to connect my laptop to my fiance's XP machine from my laptop which was running only XP at the time...it took hours and hours to get it to work right. I installed Ubuntu...entered in the proper network info...and suddenly it's all connected within minutes! Ubuntu hooks up to XP better than XP hooks up to XP! Go figure! :guitar: 

Anyway...I do have a couple small gripes...

The system exits really super fast. Too fast. It almost takes just about 5-10 seconds. Maybe some of you have experienced faster times, but when Windows XP takes almost a minute to shutdown...5-10 seconds is insanely fast. :) However...thats not my gripe...what comes next is my gripe. The process of starting up/rebooting is super slow. After the grub menu, all I see for almost a minute is a blank screen with a blinking cursor. Then it says "starting up" and that takes about 3-5 seconds and then starts loading the system with the splash screen and the processes loading. Every thread I see here for something similar is for someone who doesn't get to the grub screen or who can't use the Live CD. I've never had problems like that...so I don't know if that's a similar issue or something different. If anyone can help me with that, I'll be grateful. 

Also, back to grub...

I installed Ubuntu on a USB external hard disk, and was hoping that I wouldn't need to have that drive on when I want to run just Windows...however, grub requires it to be on in order for me to boot into anything. I'm not entirely sure how to do the fix for this that requires me to use the recovery console for Windows and use the command FIXMBR and then add Linux to NTLDR. After I get rid of Windows, this won't be an issue, but right now I still have a lot of stuff I need to do with Windows before that. Any ideas? 

Is there a way to install grub to boot from a floppy disk? That would be more convenient cause I just don't want to have to hook up the external drive all the time when all I want to do is run Windows. I've looked, but all I come up with is the NTLDR fix...which seems a bit more complex than I know how to do at the moment. Any help with that too...and I'll be eternally grateful. Not just grateful. :) 

Ok...I've written my novel. I look forward to the responses...this forum seems to be really loaded with friendly people...which is good...good for Linux and people trying to learn Linux...so kudos on that. Keep up the friendly nature of this place and other Linux communities...and before you know it...the Mac snobs (yes they are actually snobs) and the Windows people will definitely be in the minority...

---

### Post by koshari on 2007-03-29
you could use a 3rd party boot manager.

---

### Post by ArdentAdam on 2007-03-29
Thanks, but, doing a search, didn't seem to come up with much. Are there any examples you might be able to point me in the direction of?

---

### Post by sloggerkhan on 2007-03-29
I believe you can actually install grub to any partition of any disk in your computer. Maybe someone else can tell you more, but I think you could keep a grub on your actuall HD to load windows when your USB is disconnected.

A USB drive might also relate to your slow boot times if you're loading your OS off it.

Not really 100% sure about this, but pretty sure.

---

### Post by mpokrywka on 2007-03-29
To debug this booting slowdown you have to edit grub's kernel command line and remove "quiet" keyword:
1) when grub menu appears press up/down arrow to stop autoboot timeout
2) select line that says "Ubuntu, kernel 2.6.17-11-generic ", press "e" (edit)
3) select line that starts with "kernel", press "e"
4) search (left/right arrow) for "quiet" word and delete it, press Enter
5) press "b" (boot)

You should see linux kernel booting messages, try to write down last few lines when it pauses (freezes), it should give us some clue where is the problem...

---

### Post by mpokrywka on 2007-03-29
I'm not entirely sure I fully understood your remaining problems but I'll try:
Few word of explanation how grub works:
1. grub bootsector - this is 512 bytes (1 disc sector) size part of grub that runs first and tries to load so called stage 2
2. grub stage 2 - this is actual grub bootloader that supports reading files from different filesystems, displaying menu, etc

I thing that during installation you installed grub bootsector on your hard disk, but stage 2 is on USB drive. So when computer starts without USB drive, it runs grub bootsector and fails because grub stage 2 cannot be found.

To solve your problem I see 2 solutions:

Solution 1) Remove grub bootsector from hard disk - under windows this can be done with "fdisk /mbr" (don't do that yet, first run linux and read below)
This way your computer will only boot windows. If you want run linux, you will have to use additional floppy or you will have to set in bios that computer should boot from USB disk (maybe there's some friendly bios menu? F8?).
Ubuntu won't boot yet from USB disk because grub bootsector was written to hard disk.
To fix this you should run Ubuntu and run grub as root.
Under grub prompt enter "root (hd" and try autocomplete with TAB TAB.
There should be two hd: hd0 (your hard disk) and hd1 (USB disk). Type "1" and press TAB TAB to get partitions on this disk. There should be something like:
```

 Possible partitions are:
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x82

```
If you see ext2fs you are at home. Type 0 (ext2fs partition), tab, Enter: whole command will be root (hd1,0)
Next command is to write grub bootsector to USB disk: "setup (hd1)".
From now if you choose booting from USB hdd in bios, linux should run without problem.
If you desperately need grub floppy I can give instructions but this post is already too long.

Solution 2) Install grub stage 2 on hard disk - this requires additional partition on disk. You can shrink your NTFS (Windows) partition using Ubuntu install CD and create small (100MB?) partition where grub stage 2 will be stored. After creating partition (ext2) you will have to make "grub" directory on it and copy there grub stage 2 files - from /lib/grub/i386-pc.  You can also copy there menu.lst file from USB disk.
This way there will always be grub menu while booting and if USB disk is not connected then linux booting will fail when choosen from menu.
There is of course little short of details how to resize/make partition/copy files - ask if you are not sure

---

### Post by ArdentAdam on 2007-03-29
Heh...sorry to do this, but I figured out a way to solve my boot manager problem...

I found a version of grub that sits in the Windows root directory (usually C:/) and it comes with its own version of menu.lst. The instructions were to make a reference to this version of grub in the Windows boot.ini file. Then it shows up in the NTLDR boot manager at bootup. Then you enter in the information from the original menu.lst in the Linux /boot/grub/ folder. It takes a little messing with...as the program (or commands) were designed with Knoppix in mind...as I understand it...the Knoppix command line structure is a bit different...so I had to change some things, but ultimately, through some simple trial and error...I got grub to be chained to NTLDR instead of NTLDR linked to grub. 

Once I got this setup to work and load Linux...then I simply went into the Windows Recovery Console and wiped the MBR and rebuilt it. This, as I had figured, also took out access to the Linux partitions on my USB drive. So I used the alternate install disk and reinstalled grub to a different partition...which of course now means I never had to do any of this extra work, but I went and got myself knee deep in it...I figured I might as well see if I could get myself through it and get it working...which I did. 

If anyone is interested, the site where I found this version of grub at can be found here: [http://www.icpug.org.uk/national/linnwin/step1-xp.htm](http://www.icpug.org.uk/national/linnwin/step1-xp.htm)
It's a few years old...so the author might not be aware of Ubuntu...or Ubuntu might not have been released yet as of the writing of the site.

Anyway...I now know it was as easy as simply installing grub to another partition, but I like a challenge. :) 

Thanks for the help though everyone...I appreciate any and all responses.

---

