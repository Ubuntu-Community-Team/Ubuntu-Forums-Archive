---
title: "Installation of Ubuntu"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by manas on 2006-11-11
Hi
I am new to linux world.
I have PC Celeron 1.7 and Windows XP pro on it. I want get rid of XP pro and install this ubuntu software with all feature.
Yesterday I download the ISO mirror from the server of the North burned the CD and try to boot it from cdrom. I was not able to that.
Any one who help me to install it.

Manas

---

### Post by Ecthelion on 2006-11-11
Hi and welcome to Ubuntu...

Did you checked in your bios that it is set to first boot of a cd and only then from a disk?

If you did and it still doesn't work, or if your pc can't start up from a cd, then you might want to look to [this thread...]("http://www.ubuntuforums.org/showthread.php?t=294178")
It's from someone who had trouble booting from a cd...

... The last post conatains a possible solution to the problem

---

### Post by Liolikas on 2006-11-11
It may be 2 problems:
1) check in your PC BIOS cd-rom must be as "primary boot device".
if cd-room is not boot device at all change it to primary boot device. If you do not know anything about BIOS find someone who can help to you. You can enter PC BIOS by presing "delete" or "f12" button just after turning on pc normaly.

OR (if not 1)

2) you burned in bad way or downloaded with errors. download and burn cd again.

---

### Post by Drakkor on 2006-11-11
Check the md5sum of the download to make sure it's not a corrupt download

---

### Post by ReaderRat on 2006-11-11
Was the ISO image burned as an **image** file and not as a **data** file? Do you have 256 Megs RAM? On the Live CD (once booted) run the MD5 checksum test (on the menu) to be sure you have a good copy.
Post if you still have problems.

---

### Post by manas on 2006-11-11
I have burned the alternate iso image from the server.
I made changed the booting seqeuece in the bios mode first boot as cdrom.
Since its not able to that windows XP loads up by default. I tried in safe mode.
Do I have format the disk. If yes let me how to do it and installtion steps of Ubuntu.

Thks

---

### Post by ReaderRat on 2006-11-11
1)-Download the ISO file.
2)-Burn the ISO file as an **image**, **not** as a data file
3)- Burn it at a slow rate - 4X - to get a good copy.
4)- You must have 256Megs RAM for a full install. You must have 192Megs RAM for an alternate CD install.
5)- Set the BIOS to boot first from CD-ROM.
6)- Put the CD in the CD-ROM drive and reboot.
7)- Run the option to check the disc files (on the menu).
8)- Run the install option (from the menu).
9)- You should be installing Ubuntu now...

---

### Post by louieb on 2006-11-11
Here are the common reasons why a computer does not boot to a Linux live/install CD.
[LIST=1]
[*]The iso file is corrupted. Not much you can do but download it again. Check the MD5SUM.

[*]The CD is corrupted scratched, cracked,  toasted. Again not much you can do but burn or buy another one.

[*]The iso file was copied to the CD as a file, not as an an image. You can tell when you browse the CD and all you see is a single file named whatever.iso. (If you burned it as an image you should see a bunch of different files and folders.  If your not sure how to burn the file then I suggest you get a copy of BURNCDCC. You can get it at [http://www.terabyteunlimited.com/utilities.html](http://www.terabyteunlimited.com/utilities.html)

[*]The computers boot order is to boot to the hard drive and then the CD drive.  The computer should be set to boot to CD drive first. When the computer boots up there is a period of time that if you press a certain key (<del> or  <esc> are common) the BIOS setup menu is displayed. Somewhere in the BIOS menu (where depends on the computer and BIOS manufacturer) is place to specify the boot order.
[/LIST]

You have check all the above and the computer still won't  boot to a  CD. There  are a lot of computers that will not boot to a Linux CD.  I guess the gang from Redmond paid them off.

The next thing to do is make a Smart Boot Manager floppy.  Note if you replace CD with floppy in the statements above it will be more right that wrong.

How to make a Smart Boot Manager floppy:

[LIST]
[*]The first thing you need to find and download is a program sbm.bin also sometimes called sbm.img or sbm.dsk It is apparently not being maintained. If you try the SBM homepage  the download link is broken. any way you can get it here.

[*][http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk](http://slackware.at/data/slackware-current/rootdisks/sbootmgr.dsk)
[*]In linux insert a floppy and at the terminal dd if=sbootmgr.dsk of=/dev/fd0
[*]In windows get a copy of RaWriteWin here. Instructions are on the page.
[*][http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)
[/LIST]
Now insert your floppy and CD in the computer and reboot.
When the Smart Boot Manager menu displays press the down arrow until your CD rom drive is highlighted and press enter.
It may ask you a question or 2 or even  display an error message. Don't worry just press enter and soon the computer will boot to your Linux live/install CD.

---

### Post by Ecthelion on 2006-11-12
So just like I said in my first post...

You can find that also [here]("http://www.ubuntuforums.org/showthread.php?t=294178")

Just look at the last post...

[QUOTE=last post]1. downloaded memdisk and sbm.bin

Code:

wget [ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/memdisk](ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/memdisk) wget [ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/sbm.bin](ftp://ftp.mcc.ac.uk/beta/local/teaching_cluster/disks/sbm.bin)

2. copied both files to: /boot
Code:

sudo cp memdisk sbm.bin /boot

3. Edited /boot/grub/menu.lst file with vi and added three lines at the bottom of the file
Code:

sudo vi /boot/grub/menu.lst Add: title SBM-Boot a CD kernel /boot/memdisk initrd /boot/sbm.bin

4. reboot my machine and wait for the grub countdown (if the countdown is too fast, read this: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_the_timeout_seconds_for_](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_the_timeout_seconds_for_) GRUB_menu_on_boot-up
There is a menu entry for SBM, and when choosen, all works great. Thanks for the help
[/QUOTE]

---

