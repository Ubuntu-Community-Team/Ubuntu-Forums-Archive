---
title: "Before I Triple Boot: Is the wiki up-to-date?"
date: 2009-10-27
forum: Apple Hardware Users
---

### Post by Who on 2009-10-27
Hi,

Before I start working through to follow the instructions, can someone tell me if I should have faith in 

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I want to triple boot OSX, Ubuntu and XP, but using Ubuntu or XP will be very rare, so I want to keep the Apple bootloader intact, and just hold alt when I want to choose OS.

I plan to do the following:

1. Use Bootcamp to make some space for XP
2. Use Disk Utility to shrink my OS X partition to make space for Ubuntu
3. Use Disk utility to split the Ubuntu partition so that I have /, /home and swap
4. Install Windows using Bootcamp, install drivers, etc
5. Install Ubuntu (reformat /, /home to ext3, swap to 'linux swap using gparted) (put GRUB on the partition that is '/' for Ubuntu), install drivers, etc
6. Use reFIT live CD to fix whatever it is the ubuntu breaks (i.e enter the partition tool and resync partitions) - is this reqd?
7. Sleep

Anyone have any reasons to believe that wouldn't work or that I've not understood the wiki?

In return for help now, I'll write up a modern howto if it works well :)
Thanks
Who

---

### Post by borovy3488 on 2009-10-27
That is the guide I followed.  However, I did get some problems and I'm working on fixing them.  I got windows installed, then tried to install ubuntu.  My refit will not show ubuntu, nor will it boot windows after the ubuntu installation.

Working on the fix now.  I've tried multiple solutions, none working yet.

It does work without refit.  You just have to hold 'opt' on boot, then select windows.  It will load grub, then choose either Ubuntu or Windows and they'll boot.  Mac is listed too, but it fails to boot.  If you can get refit to work, show me your secret!

---

