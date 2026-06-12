---
title: "The GRUB Keeps Breaking"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by rockstar on 2006-09-22
ok, I've read a bunch of posts on how to fix the grub including this one:
[http://www.ubuntuforums.org/showthread.php?t=263110](http://www.ubuntuforums.org/showthread.php?t=263110)

But nothing works.  I plopped in the Windows Xp Cd and reformatted the Hard drive, but then after that I realized that Linux couldn't have effected my NTFS partition anyway.  So I used the Windows Cd to reformatt and install most of windows, but when I restarted to continue the installation, I got a DRIVE READ ERROR message.

I took this to mean that there was no boot loader at all.  I thought that windows would replace the boot loader when I installed it but it didn't.  So I got my Ubunto Live CD and booted live off of that. Then I typed

sudo cfdisk /dev/sda

Then I changed the primary boot device, saved it and restarted.  That made it so that just my Windows booted.  So I went back and loaded the Live Cd again and then reinstalled my GRUB.

[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+grub+install](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+grub+install)

So, This brought me back to the beginning, my windows won't boot at all but nothing is wrong with Linux.

My favorite command is 

sudo gedit /boot/grub/menu.lst

I've added all kinds of entries to the bottom and none of them work, I've changed the (hd0,1) over and over,  I've tried sda instead too.

I'm out of ideas.

---

### Post by bulldog on 2006-09-22
I'm not:D 

I understand you have two hdd's and windows has an habbit that it wants to boot from the first hdd.

If you explain a little more what you want to achieve,I could be of some help to you. 

Reading your post again I make some asumptions.

You want a dual boot system with GRUB.

Set the windows hdd as first boot and install Ubuntu on the second hdd.
GRUB will be written on the first boot hdd [windows] and put an entry for Ubuntu as well as your windows install.

Another option is set your Ubuntu as first boot so GRUB installs on it.
Put windows on your second hdd,but make it first the boot hdd so it won't mess with GRUB.

Then when done installing put the Ubuntu back as boot hdd and put the following at the end of your menu.lst:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by rockstar on 2006-09-22
Alright, I have one hard drive.

It has four partitions

This is what CfDisk says:

 sda5                    Logical   NTFS             []              22010.85
    sda2                    Primary   Linux ext3                        9516.65
    sda3        Boot        Primary   Linux swap / Solaris              1093.97
    sda4                    Primary   W95 FAT32                        67397.95

All I want to do is be able to boot both windows and Linux.  No matter what I add to the GRUB config files will it let me run windows.  I know Windows works but I don't know how to boot it.

It booted and then I re-installed the Grub and it stopped working again.

---

### Post by rockstar on 2006-09-22
Also, no matter what I do in cfdisk the Grub still won't boot windows.  I booted windows before I re-installed Grub, but now I get all sorts of Grub Errors.  I've checked all the Grub errors on the Grub Errors page.  Something's just not adding up

---

### Post by bulldog on 2006-09-22
Okay my asumptions where misstaken.:D 

But doesn't need windows a primary to boot?

What I see is linux primary
swap primary [not needed]

Logical ntfs [windows?]
W95 Fat32 primary

Where is sda1 gone to?
Do you have a windows 95 OS?

What should you do with an NTFS partition?
Windows95 can't read it.

Something els what could matter.
Boot into Ubuntu and do

sudo fdisk -l [this is a l as in like and not a 1]

and make a note of the names because grub and menu.lst have different names  for your partitions,and also fstab is something to think about!!
So you have the names as Ubuntu sees them and which you should use in menu.lst

---

### Post by rockstar on 2006-09-22
There is one NTFS, the sda5, thats the windows partition.  I've booted with this setup before, I know all of the OSES work, but not together, the GRUB is the problem

---

### Post by bulldog on 2006-09-22
Grub is not a problem but I have to get clear how you divide your hdd.

What kind of windows do you have XP or w95?

XP should boot from a primary as far as I know and that's not the case.

If you want it working you should start from scratch.

If possible make a primary and install Windows.

Make room for Ubuntu but don't format it leave it as allocated space.

Install Ubuntu and in the end it installs GRUB and you get an entry for XP.

---

