---
title: "Installing Ubuntu on Second (SATA) Hard Drive"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by geordietodger on 2007-08-04
Hi all
I have spent hours reading similar threads but don't seem to be getting a definitive answer.

I currently have a 200GB SATA drive which has Windows Vista Ultimate on it.

I have a second 80GB SATA drive that is empty at the moment and it is where I would like to install Ubuntu.

Assuming I choose the second drive to install Ubuntu on - is this going to give me a boot menu where I can choose either Ubuntu or Vista?

I have read a bit about GRUB and this seems to be the way to go but most of the thread I have read have either been to do with partitioned installs and/or IDE hard drives.

Ideally I do not want to start unplugging drives when I want to run Vista/Ubuntu - I just want some kind of menu.

If anyone can help me out it would be much appreciated!

---

### Post by dorath on 2007-08-04
What you want to do is similar to what I did, but with XP and 7.04 instead.

First I installed XP on one drive, just like you've got Vista on one drive.  Then I opened up the case and disconnected the power to the drive with XP.  Started the machine back up and installed 7.04 on my second hard drive.  Personally, I didn't want to risk GRUB messing with my XP drive at all (yes I could probably fix it if something did happen, but I didn't want to chance it).

After 7.04 was installed, I plugged the power back in for the drive with XP.  At this point I could tell the BIOS at startup which drive I wanted to boot to, but ntldr and GRUB only had the option to boot into one OS each.  Not good enough!

After some digging around, I found the following instructions:
[LIST]
[*]Tell the BIOS to boot the drive with 7.04 first
[*]Boot into 7.04, and open a terminal window
[*]Make a backup of your menu.lst```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```
[*]Open menu.lst to add an entry for Vista (I will use pico as a text editor, you can use whatever you like)```
sudu pico /boot/grub/menu.lst
```
[*]Enter the following at the bottom of the file:```
title           Vista
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
rootnoverify    (hd1,0)
savedefault
makeactive
chainloader     +1
```
[*]ctrl+x to close, save your changes!
[*]Reboot, cross fingers, look for the Vista option.
[/LIST]

---

### Post by geordietodger on 2007-08-04
jeez!  didn't realise it was going to be as complicated!  Sorry am a complete new comer to this scene.  Maybe I would be best just sticking Ubuntu on a spare laptop

---

### Post by logos34 on 2007-08-04
Check out this page (and the links to dual-boot on 2 drives):
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

The ideal setup would be to boot to Grub menu screen on the 80 GB ubuntu drive and from there to choose either linux or vista on the 200 gb drive.  Set your 80 gb drive first in the Bios hard disk boot priority before you begin the installation.  That way grub will go by default on the MBR of the ubuntu drive (which will be 'hd0').  It should detect vista on the other drive and add an entry to menu.lst--hopefully with the correcct mapping.  Doing it this way means grub won't overwrite the vista bcd bootloader, so if you ever have a problem getting linux to boot you will be able to switch the bios order and boot into windows.

---

### Post by geordietodger on 2007-08-04
cheers Logos, that sounds a little easier.

---

