---
title: "HP Pavilion Recovery Partition and Grub"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Wilbur Kelly on 2007-01-28
Hi,
I just completed installing 6.10 on a HP Pavilion which came with a 250GB HD.  HP instead of providing a CD of windows, provides a "Restore Partition" which is accessed via a bootloader screen which blinks on and then boots 3 seconds later into the OS it came with: Windows XP Media Edition 2005.  I have been playing with the Live CD and reading various forums and noted that on another forum there was a problem with the dual boot with the install on the HP Pavilion due to this setup. I don't have the details and they probably don't matter since it was another distribution.  I decided it might make the installation less likely to fail, since I really didn't know what I was doing, to install linux to a second hard drive.  My supplied HD is 250 GB a SATA.  I had on old 200GB IDE and I plugged it into the cable just below my DVD player.  I used Maxtor MaxBlast 3 and it would only let me make NTFS partitions.  I made 2, and then windows did recognize them.  

I put in the Ubuntu Live CD and chose install.  When I got to Gparted I played with the second disk and make a 94 GB ext3 partition, a 1GB swap partition and have the rest set up as NTFS but plan to change that to a FAT32 in increments of 32GBs as a way to have things I can swap between installs.  Anyway, the problem is:

When I boot up I see the windows bootloader screen that gives me the choice of 1)restoring the machine to the way I got it new from HP and 2) booting into Windows XP Media edition.  I never see GRUB.  I know I chose where to install Ubuntu and I know it worked because:

I played with the bios screen and am not sure now what I did but several layers deep somehow I triggered what I think must have been my Grub screen since I saw windows and Linux as choices.  I chose Linux and everything came up fine in Ubuntu.  I was even able to download the 113 updates.  But when I next tried to reboot, there are the widows choices only.  

I am sure that this is not too bad.  I have made a floppy that has Windows boot.ini on it and it has nothing about Ubuntu and I am sure that that is one way to fix the problem.  That would be one fix, to edit boot.ini to give me the choice of booting to ubuntu.  I don't really know enough about this even if it seems like I do because I think what I have said is accurate.  First of all, with the differences between how windows and linux names hard disks I am not sure I could edit it correctly. But my preferred fix would be to have GRUB come up first and then hand thing off to the microsoft bootloader (if I wanted to work with XP), which I think is possible based on something I read in some forum somewhere but which I haven't been able to find again.

I know this is somewhat rambling but I wanted to provide enought information to describe how I got where I am.  I appreciate any help.

wk

---

### Post by mikewhatever on 2007-01-28
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
Please check out that thread for more info. Ubuntu installation on the second HD can be tricky indeed.

---

### Post by dbbolton on 2007-01-28
when i installed ubuntu on my pavillion, grub looks like this:

Ubuntu Kernel A
Ubuntu Kernel B
Ubuntu Recovery Mode
Ubuntu memTest
Other OS:
Microsoft Windows XP Home Edition
Windows NT 2000


the windows nt 2000 boots the recovery partition. (my windows calls it drive D: )

---

### Post by Wilbur Kelly on 2007-01-28
Thanks Mike,
I have gone to the page and am printing it.  It does look a little complicated. I will be first reading and then working on it.
wk

---

### Post by Wilbur Kelly on 2007-01-28
Thanks DB, 
I am not sure how to look at grub yet.  Your pavilion has the HP Recovery partition? That is probably important.  I don't know if all pavilions do.
wk

---

### Post by Wilbur Kelly on 2007-01-28
I want to thank everybody. The problem seems solved. 

Mike suggested a link.  When I read the first page I thought: Gosh, I wish I had done it that way; it seemed so easy... And, if I understand right, somehow I achieved something similar without doing it the way it suggested:  "first, disconnect your Windows drive, then connect the drive you want to install ubuntu on as the primary/master drive"...  

I have NO IDEA how it worked out the way it did but apparently I was booting into the windows bootloader which had no knowledge of my Ubuntu install because Grub was loaded onto the second hard drive.  I had, as I described in my first post, stumbled onto how to get to grub on a screen several layers deep in the BIOS.  That screen, it turns out, was the hard drive boot order.  If the boot order is set up for booting to the original drive, SATA, it has no knowledge of the second IDE (slave) drive and it goes blithely on it's way into XP.  If, in that screen, I chose to make the IDE drive the first to look at and boot from, then I get to see GRUB and can boot to either.  By saving that boot order, I can come up into GRUB everytime and chose "where I want to go to today".  

I don't know that I need to change anything since it appears to be a working system the way I have it set up.  Does anyone see any reason to change the way it is setup to the more conventional one, with GRUB on the original boot drive? 

There is one small detail I'd like to fix.  The HP Recovery Partition is not so named in GRUB.  It is called: Windows 2000 or XP.  I'd like to fix the description which I suppose is in the GRUB file somewhere.  How do I get there and how dangerous is it to mess with/edit at this point.  Should I leave well enough alone? I'd like to know how to look at/ view the file, even if it is best left alone.

My first post was from Windows, this is from Ubuntu.  Cool.

Thanks again.
wk

---

### Post by Buck2348 on 2007-01-29
```
gksudo gedit /boot/grub/menu.lst
```
The line you want is near the bottom of the file.  I shouldn't think it would do any harm to change the title.  You don't plan to use grub to boot into it do you?  On my Dell the recovery partition is the third partition on the master drive.  It did not get listed in grub, but it is auto mounted as /media/hda3 and displayed on the Desktop and in Places as DellRestore.  I suggest you  don't do anything to disturb the partition as you never know when you might need it.

Buck

---

### Post by Wilbur Kelly on 2007-01-29
Hi Buck,

You were right.  It didn't do any harm to change the title.  I tried and it worked fine. No, I think if I were to really want to try the restore the partition for any reason I'd change the boot order and probably unplug the IDE Drive for safety's sake.  I appreciate your advice. Given the lack of a Window's Disk, I plan to leave the restore partition in place though I did make a backup of the partition, just in case...,(belts and suspenders)

I really do appreciate everybody's help here. I've wanted to change to Linux for YEARS and got Mandrake up about 3 years ago but couldn't get the usb wireless connection to work on my home net and let it slide.  When I was able to connect to the wireless access point using the LiveCD, I knew the time had come.  Thanks again everybody.
wk

---

