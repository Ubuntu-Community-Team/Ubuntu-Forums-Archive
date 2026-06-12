---
title: "Dual boot on two hard drives?"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by symbiont7 on 2006-06-15
So I want to play around with ubuntu and I tried running off the CD, but it is quite slow as everyone I'm sure knows. I definitely want to dual boot at this point so I can test things out, I'm not ready to leave WinXP Pro just yet. I've scanned the forums and a few things online about dual booting, but I haven't seen anything relating to using multiple drives.

I have two drives in my current rig, each on a separate IDE channel (no slave of course). One off the mobo, one off a Promise ATA/IDE card. I can run a master/slave combo if that's easier for some reason. The "main" drive is partitioned into a "system" partition (OS and apps) and "docs" partition (the target for "My Documents" actually), and the second drive is a single partition "backup" drive, where I keep various documents backed-up and it also gets used for Photoshop/Video swap space.

So can I just leave my first drive alone, and wipe clean and install ubuntu on the second? Or along the same lines, leave it all as-is and add a third drive for ubuntu? The WinXP install is probably 6 months old, I usually reformat every 6 or 12 months because well, I'm weird like that!

---

### Post by yager on 2006-06-15
While you are not using an external drive, the following thread may give you some ideas on what it would take. [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

What you want to do is perfectly possible as long as you format the correct device and as an idea to keep things completely isolated, you may want to install GRUB in the MBR of the second drive.  This would leave your XP drive pristine in case something goes horribly wrong.

To really cut down on the antacid moments, you could remove the XP drive from the system if you want to open your case and proceed with the clean install from the CD.

When you reconnect the Windows drive after the install, you control which operating system your system boots from by changing the hard drive order in the BIOS.   At boot up, go into BIOS, change the order and boot to whichever operating system you want.

---

### Post by symbiont7 on 2006-06-15
Hmm...the whole "disconnect the main drive" thing sounds like a great plan, sounds super easy too.

So I disconnect the WinXP drive, do a standard install of ubuntu on the 2nd drive (vs. what sounds like to me a more complicated dual boot set-up) and that's that? Hook 'er all back up and just control it all from the BIOS? Man that sounds easy.

How does a dual boot system start-up in a single drive install? I'm guessing GRUB has something to do with it. I should search and do some reading about that!

Thanks for the help!

---

### Post by someusernoob on 2006-06-15
Best way:

- Install XP on any disk (or if its installed allready, skip this)
- Set your XP disk as Slave, it will boot up anyway.
- Install Ubuntu on your master disk. Now you can just boot with Grub, without loosing the MBR on the XP disk. with Grub you can choose between Ubuntu and XP, it automaticly detects.
- If you dont want Ubuntu anymore, just rip out the disk, set the XP disk as master, and format or whatever you want the disk with Ubuntu on it., There will be no trace of it after that.

It wont work if you install Ubuntu on say disk2 while disk1 is disconnected. When you put in disk1 after that, Ubuntu wont boot up, because he cant find the root file system (/dev/hda and /dev/hdb are changed). Unless you want the Ubuntu disk as master, but then there is no point on disconnecting the XP disk at all. When you leave it on, you can easilly set mountpoints for it during the installation, so that saves you some time on searching the internet on how to automount the disk.

And switching OS with the bios is really annoying, and really not necesarry.

A little example:

```

IDE1: 
Master - Disk1 (Windows XP)
Slave - Disk2 (Empty > supposed to install Ubuntu)
IDE2: 
Master - CD/DVD-rom drive
Slave - 2nd CD/DVD -rom drive or 3rd harddisk or empty

Now change it to:

IDE1: 
Master - Disk2 (Still empty > > supposed to install Ubuntu)
Slave - Disk1 (Windows XP)
IDE2: 
Master - CD/DVD-rom drive
Slave - 2nd CD/DVD-rom drive or 3rd harddisk or empty

```

And install Ubuntu on the IDE1 Master disk.

 If you want to get rid of Ubuntu after that just go to situation one and format the drive in XP.

---

### Post by symbiont7 on 2006-06-15
I appreciate more advice, but IMHO swapping out which hard drive will boot first via the BIOS thus determining which OS I'm booting with isn't that much of a pain, especially since I only want to test out ubuntu. This way seems to leave my system perfectly clean if I decide to wipe the second drive (which would then contain ubuntu) later down the road.

Hang on...light bulb flickering...maybe I'm starting to get your method. I put ubuntu and Grub on the same disk, and since it's the master disk Grub kicks in, let's me choose which OS?
[edit]
But can't I do the same thing by setting the boot order in the BIOS to crank up the ubuntu/Grub disk first and skip all this slave/master stuff? Remember, I have plenty of free IDE channels to keep them all master.
[/edit]

And that doesn't write/change/put a hex on any of my WinXP stuff on my (now) slave disk? I want the 2 OS's to NOT share ANYTHING between disks at this point.

Thanks for the help!

---

### Post by yager on 2006-06-15
[QUOTE=symbiont7]How does a dual boot system start-up in a single drive install? I'm guessing GRUB has something to do with it. I should search and do some reading about that![/QUOTE]

You are catching on fast.  GRUB is a replacement for Microsoft's Master Boot Record routine.  On a single drive system, there would be at least 2 partitions, one XP and the other Linux.  GRUB sits in the very first sector of the drive and waits for the hand-off from the BIOS.  Once it starts, it presents you with a menu to choose which kernel and or operating system to boot and where it is located on the drive.

You can eventually use the Dual boot method that everyone else uses with only a small change to one file.  In your case, you would leave your system to boot on the Ubuntu drive first and then add in the following commands to the GRUB menu to tell it to boot from the other drive when you choose XP.  Here is the code you add to the /boot/grub/menu.lst file AFTER the ### END DEBIAN AUTOMAGIC KERNELS LIST line.
```


title		Windows XP
root		(hd1,0)
map		(hd1) (hd0)
map		(hd0) (hd1)
makeactive
chainloader	+1
boot
```

I would propose this as phase 2 after you are a happy Ubuntu user.  If you find that Ubuntu is not your cup of tea, which we all know will not be the case, ;) you simply change your BIOS back and format the Linux drive from inside XP.  No fuss, no muss,  but you won't be going back...

Just a word on kernel updates though, sometimes you will find that a kernel upgrade will get the configuration of the drives wrong in the menu.lst file.  If that occurs, you will need to edit this file again to correct any mistakes made during the automatic portion.

If you want to know more about GRUB, go to this link.  It has all you will ever want to know about GRUB.  I am still learning this stuff.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

If you want to access your XP drive from inside Linux, that is another thread.  Look up the mount command.  Read Only access for NTFS is a standard part of Linux.  If you want more, there is a tool ntfsfuse but I have no experience with that.

Have a great day.

---

### Post by xeero on 2006-06-15
I'm triple booting with two hard drives on the same IDE in my system.  this way, i can keep Win XP, my favorite linux distro and a test distro on my computer at the same time.  i love it!  i use grub to select which OS to boot.  you don't want to have to change the BIOS for something like that.  plus, i password protect my BIOS so it would be even more hassle to change it frequently.  

whatever happens, if you decide to toss linux, you can always boot from your Windows Startup Disk and enter "fdisk /mbr" at the command prompt to get back the Windows bootloader.  then you can reformat the second drive for windows.  

but, with the many linux distros today and with your computer skills, i think you'll find a distro you can use daily.  i rarely boot into Windows.  anyway, here's my setup:

```

Drive 1 (master):
  Primary partition:
    hda1 - Win XP Pro
  Extended partition:
    hda5 - fat32 partition for windows/linux data

Drive 2 (slave): 
  hdb1 - Ubuntu 6.06
  hdb5 - Mepis 3.4-3
  hdb6 - ext3 partition for linux data
  hdb7 - fat32 partition for win/linux data
  hdb8 - swap partition
```

what i find is that lately the linux installers are pretty good about finding the Windows OS and will add it to the grub menu.  more often, they may miss another Linux OS in the system, which is fixable too.  in either case, you can edit the /boot/grub/menu.lst file to add the other OS's.  for adding Windows to the list (if it's not there by some chance), you should be able to easily find help here or elsewhere on the Net.

---

### Post by FuriousLettuce on 2006-08-22
It's definitely handy to have two seperate hard drives if you're a bit cautious about dropping windows. It is perfectly possible to install ubuntu completely seperately on the second hard drive if you want, without touching your XP disk (as suggested, if you're worried, disconnect the XP disk before you install) and then use the BIOS to switch between. 
In fact, some motherboards actually give you the option to choose which device to boot without actually changing anything. For instance, on my computer I currently have XP & Vista installed on seperate drives, and if I hit escape during the POST screen, I simply get a menu which hard drive to boot. If I don't press anything, it just loads XP.

The other way to do it is grub, which is a really good way of doing it. As mentioned, simply connect your XP as slave, and install ubuntu on master - this will leave your XP disk in pristine condition, but allow you to use grub to switch between.

EDIT: Didn't notice the thread ended in June...

---

