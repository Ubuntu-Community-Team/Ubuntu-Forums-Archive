---
title: "will this work?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by shssta on 2007-02-15
ok i got a copy of 6.06 ubuntu from my cousin and i cant get it to work, heres the specs on my system

emachines w3050
AMD sempron 3000+
1.99 Ghz
512 Mgs ram
80 gig master HD, 40gig slave HD

so what id like to do is use the 80 gig for windows and dual boot ubuntu on the 40 gig, can i even do that or do both boot partitions have to be on the master drive? and also when i try to boot off the Cd i can hear it start to spin but it jumps strait to Hd boot, the cd was burnt correctly because i can view the files on it, i even went into bios and only put in boot from Cd as an option but then it just stalls, ill d/load a new copy or request one if need be but first off id like to know if what im trying to do will work, i dont want to lose windows in case something doesnt work with ubuntu, plus i have a lot of software i use on windows i dont want to ditch yet, any advice would be greatly appreciated.

---

### Post by FyreBrand on 2007-02-15
1. First before you try to install Ubuntu backup your Windows system.  Anytime you ever partition a hard drive or install a new boot load (Ubuntu will install GRUB) there is a risk that partitions can be corrupted or broken.

2. In some, especially older BIOS, the boot from CD-R drive needs to be the first option available.  Typically when the computer boots from the boot order list it takes the first available bootalbe media.  So if the options go:
[INDENT]a. Hard Drive
b. Floppy Drive
c. CD/DVD Drive[/INDENT]
It will boot to those in that very order.  So try that first and make sure the your CD Drive is the first one on the list.

3. The tricky part to this is installing a dual boot where Ubuntu is on the slave (second) IDE drive.  Once you get the first part straightened out here is a thread on dual booting on two drives.  It is a bit complicated so make sure you read it carefully.  Ask questions there before you try it.  It's not a trivial task.  Here is a link to that thread: [**Dual Boot 2 Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902").  There are also other threads discussing how to do this and problems people encountered.  I would encourage you to do a forum search.  Keywords: drive, dualboot, two.  Other searches that might be helpful: dualboot, partition, grub.

Good luck.

---

### Post by pozitron969 on 2007-02-15
Should be no problem to do what you are asking.  The only thing is to make certain that the installer doesn't write over your 80 GB drive.  As I understand it Windows is the only one that will require you to put the boot partition on the master drive.  Some distros of Linux will auto detect Windows on the drive and automatically select the other drive, so you shouldn't have any problems.  Fire it up and join the party!

---

### Post by seshomaru samma on 2007-02-15
yes you can dual boot windows and linux , linux doesnt have to be on the master
you should however back up all your data if this is the first time you install 
please read this [guide ]("http://www.psychocats.net/ubuntu/installing")
i couldn't find a dualboot guide ,maybe someone else can post one.

if you are sure you set the bios correctly (you can try another bootable cd to test it) then the reason is probably you didn't burn the disc correctly , you have to burn it 'as image'
another possibility is that the burning wasn't successful, try to burn a copy at the slowest possible speed.

---

### Post by igknighted on 2007-02-15
> **shssta said:**
> ok i got a copy of 6.06 ubuntu from my cousin and i cant get it to work, heres the specs on my system

emachines w3050
AMD sempron 3000+
1.99 Ghz
512 Mgs ram
80 gig master HD, 40gig slave HD

so what id like to do is use the 80 gig for windows and dual boot ubuntu on the 40 gig, can i even do that or do both boot partitions have to be on the master drive? and also when i try to boot off the Cd i can hear it start to spin but it jumps strait to Hd boot, the cd was burnt correctly because i can view the files on it, i even went into bios and only put in boot from Cd as an option but then it just stalls, ill d/load a new copy or request one if need be but first off id like to know if what im trying to do will work, i dont want to lose windows in case something doesnt work with ubuntu, plus i have a lot of software i use on windows i dont want to ditch yet, any advice would be greatly appreciated.

Ok, do this to avoid any complications (once you get a working CD that is):

1) set the bios to boot CD first.

2) install ubuntu such that it is only on only the 40gb drive (very easy)

3) the last screen before the install it should come up with a screen saying what it is going to do.  There will be a link saying it will install grub (the bootloader) to (hd0).  Click it and change it to install to (hd1).  This is not critical, just a convenience.  if you mess Ubuntu up or decide to get rid of it, there will be no messing around to get the windows bootloader back.

4) once the install finishes and you reboot the system, change the hard disk priority in the bios to boot the 40gb Ubuntu disk.

5) to view and modify files on your windows disk you will need to install ntfs-3g.  It is experimental, so be aware it could damage your windows file system.

6) there is a driver, I can't remember the name, that installs on windows and lets you edit/view your linux files from windows.  This works great, I have used it.

7) aside from that you should be OK, Ubuntu should see XP and set up the bootloader to give you a choice at boot which to use.

---

### Post by shssta on 2007-02-15
ok some good info here, i set all the boot options to cd and that didnt work it just stalled, another thing is i recently had a severe crash in XP and had to reformat the whole thing and i think the disk worked before that i just didnt have the HD space to put all my windows stuff on one HD but after the format I had more room because i lost a ton of media files, so i moved everything to the main drive, so another question, if it does in fact corrupt my windows partition, i should be able to reinstall windows again fresh on the master without a problem? i know it will be a headache but as of right now its just a matter of reinstalling everything, not a whole lot of personal files that i will lose

---

### Post by FyreBrand on 2007-02-15
> **shssta said:**
> ok some good info here, i set all the boot options to cd and that didnt work it just stalled, another thing is i recently had a severe crash in XP and had to reformat the whole thing and i think the disk worked before that i just didnt have the HD space to put all my windows stuff on one HD but after the format I had more room because i lost a ton of media files, so i moved everything to the main drive, so another question, if it does in fact corrupt my windows partition, i should be able to reinstall windows again fresh on the master without a problem? i know it will be a headache but as of right now its just a matter of reinstalling everything, not a whole lot of personal files that i will loseIf something goes really wrong you should be able to reinstall Windows with no problem.  It will write over the boot partition and will give you the option of formatting one or both drives.

So your BIOS is being a bit tricky on booting it seems.  It's really hard to give suggestions without seeing the BIOS first hand as there are so many little variations between versions and vendors.  There are a couple things you could try.

1.  Make sure you are saving your BIOS settings on exit.  Please don't be insulted because it sounds so obvious but sometimes in a rush to change a BIOS setting it's easy to escape out of the menus and forget to select the "save settings" option.  Just an easy obvious double checker there before trying other things.

2. In some BIOS versions there is a setting, outside the boot order, that says something to the effect of "boot to other device".  The setting for it is usually "enable" or "disable".  You would want to disable that setting and see if that makes a difference.

3. If #2 doesn't work or isn't an option in your BIOS then try disabling booting from the hard drive period.  So in the boot order selection menu just select "CD Drive" and nothing else.

---

### Post by shssta on 2007-02-15
> **FyreBrand said:**
> If something goes really wrong you should be able to reinstall Windows with no problem.  It will write over the boot partition and will give you the option of formatting one or both drives.

So your BIOS is being a bit tricky on booting it seems.  It's really hard to give suggestions without seeing the BIOS first hand as there are so many little variations between versions and vendors.  There are a couple things you could try.

1.  Make sure you are saving your BIOS settings on exit.  Please don't be insulted because it sounds so obvious but sometimes in a rush to change a BIOS setting it's easy to escape out of the menus and forget to select the "save settings" option.  Just an easy obvious double checker there before trying other things.

2. In some BIOS versions there is a setting, outside the boot order, that says something to the effect of "boot to other device".  The setting for it is usually "enable" or "disable".  You would want to disable that setting and see if that makes a difference.

3. If #2 doesn't work or isn't an option in your BIOS then try disabling booting from the hard drive period.  So in the boot order selection menu just select "CD Drive" and nothing else.

yep have already done all of that, my bios even has a boot menu on top of the regular bios settings and i tried that too, i just ordered another CD from ship it to see if the cd is the problem, i want to say it loaded before and when i got to the partitioning part i bailed because i didnt have my files moved over and never got around to messing with it again until yesterday, and now it doesnt work, but i may just be imagining things, so i guess i will wait and see

---

