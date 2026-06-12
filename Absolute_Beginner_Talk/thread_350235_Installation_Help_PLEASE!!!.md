---
title: "Installation Help PLEASE!!!"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by BennieBlount on 2007-01-31
I have downloaded, burned to CD, both Ununtu 6.10 and 6.06 LTS. I want to install Ubuntu on my Dell Dimension 3000 Computer. I have Windows XP on it. The installation instructions say to leave the CD in the drive and reboot the computer and Ubuntu will boot. 

When I reboot the computer still goes to Windows XP. Ubuntu does not boot and therefore I can not install it.  I have even went into the boot menu on my system and directed it to boot from the CD, but it continues to go to Wondows XP. What am I doing wrong?

 The autorun on the CD will only take me to the menu to view or install the programs, not install Ubuntu.  Is there another way of installing Ubuntu?

Frustrated,

Bennie

---

### Post by jvc26 on 2007-01-31
So you have installed Ubuntu onto the system? (i.e. booted the livecd, gone through the install process and now its rebooted and no Ubuntu?

Edit:: No, Understand now, apologies thought you were talking about a reboot after the install... You need to go into your BIOS and change your settings to boot from cd (See the post below):
Il

---

### Post by aphouser on 2007-01-31
Sounds like you just need to change your boot order in your BIOS.  When your computer is booting up you should see a message that says something like "Hit DEL for setup."

Hit the delete key as your computer is starting and it should take you into the BIOS after a minute.  Under the Advanced menu you can select your boot order.  Make sure your CD-ROM is before your Hard Drive.  (Use the arrow keys to navigate and Page UP/Page Down to change values.  Then press Escape to back up one menu level and hit Exit With Saving.

That should let you boot off the CDROM

---

### Post by jkeyes0 on 2007-01-31
It sounds like a bios setting. When you first turn your computer on, there should be an option that says something like "Press DEL to enter setup" or "Press F2 to enter setup". Once you've pressed that button, it should take you to a menu where you can change the boot order, and put the CD-rom drive ahead of the Hard drive.

Alternately, I know lots of Dells come with an option to hit F12 to change the boot order (should show up in a similar location to the "Press F2 to enter setup" prompt).

What options do you have when you first turn your computer on? (before Windows starts, right at the very beginning)

---

### Post by joselin on 2007-01-31
> **BennieBlount said:**
> The autorun on the CD will only take me to the menu to view or install the programs, not install Ubuntu.  Is there another way of installing Ubuntu?


You must have an Install icon on the desktop that must start the installation of the system.

---

### Post by jvc26 on 2007-01-31
> **joselin said:**
> You must have an Install icon on the desktop that must start the installation of the system.

He's talking about the XP autorun which you get if you put the Ubuntu cd into an XP OS. You need to boot into the cd to make it work.
Il

---

### Post by CongoJim on 2007-01-31
Or it could just be a bad CD, wouldn't be the first. Bennie, what copy of 6.10 did you download?

---

### Post by Bloch on 2007-01-31
A couple of things to check:

1. Has the disk been burned as a "disk image"? - i.e. does it have the .iso extension? 

2. A disk drive that reads disks perfectly is not neccessarily able to boot from a disk. You say you have gone into the BIOS and changed it so system boots from the CD. When it boots do you get a message ....... boot from CD failed ....... or something like that? Depending on your BIOS, you should be able to change it so choice N. 1 is CD-ROM and all other choices are NONE.

3. Have you ever booted successfully from a CD-ROM? You might try downloadiing Puppy Linux or something else. If that too fails to boot, then it might be you CD drive. But check the BIOS settings again.

Then when it starts up it will run "live" - that is from the CD-ROM. It will be a bit slow and clunky and you cannot permanantly install new programs. There will be an icon on the desktop to install ubuntu on your hard drive.

---

### Post by BennieBlount on 2007-01-31
Thanks for all the replys. I have tried every suggestion again and still no boot and no install. 

If Ubuntu will boot from the CD, shouldn't there be a "setup" or "install" file somewhere on the CD that I can just click on to start the Ibuntu install process? I can't find one.

Still puzzled,

Bennie

---

### Post by OldTimeTech on 2007-01-31
The install that you are looking for is after the Live CD brings a ubuntu desktop to your screen....at that point it will show you a install.

Unlike windows you cannot go into the cd and find an .exe and install.

It looks like either your cd is not burned as an .iso image or your cd player/reader is not reading the cd.  If you have a windows machine handy, put cd in, open my computer, find your cd and right click for the dialog box, then ask it to open and see if the file burned to the cd has .iso after it, if it doesn't it was burned wrong.  Of course if you can't see the cd in the cd player/reader it could be a bad cd.

---

### Post by BennieBlount on 2007-01-31
Thank you all for your help.

My problem was with the CD image. I burned another CD using the suggested burning software and the CD BOOTED AND INSTALLED!

Now I just have to figure out how to connect to the internet.

Thanks again,

Bennie

---

