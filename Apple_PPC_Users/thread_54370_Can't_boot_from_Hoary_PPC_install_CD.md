---
title: "Can't boot from Hoary PPC install CD"
date: 2005-08-04
forum: Apple PPC Users
---

### Post by hot_pastrami on 2005-08-04
Good morning.  Sorry for the long post, but I want to detail everything I've tried:

I am attempting to install Hoary on a Dual G4 PPC, and running into a brick wall before I even get started.  The machine refuses to boot from the Ubuntu CD.  I'm a long-time Windows user, moderate-time OSX user, and first-time Linux user.

I downloaded the ISO from a mirror linked on ubuntulinux.org, and used Nero on a Windows XP box to burn it as an image to a CD.  The directories and files all appear to be there, and the disc is readable in OSX from my Combo drive.  There is also a dead Superdrive in this box, but as this system belongs to my employer, and given that I am inexperienced with Mac hardware, I am hesitant to open it and disconnect anything.

Initially, I tried inserting the CD and holding "c" while booting, but it still booted into OSX.  I tried booting and holding Option, and it displayed a screen with the Hard Disk and the Ubuntu CD (though it shows no label under the CD drive), but if I select the CD it just flickers the screen, and returns to the same menu.

I tried booting to Open Firmware, but the standard **boot cd:,\install\yaboot** failed, maybe because it's not the first CD device.  On a guess, I tried changing "cd" to "cd2," and then it showed some text too brifly to read, and stopped on a gray circle with a slash through it.

Just to be safe, I downloaded a new ISO onto the Mac, and burned it as an image using FireStarterFX, and repeated all of the above, with the same results.

As a last resort, I booted to OSX disc 1 and used the disk utility to wipe the hard drive, and replaced the HFS+ file system with UNIX File System (since I seem to remember reading that Linux doesn't get along with HFS+).  Rebooted, tried all of the above again, no change aside from the fact that it now boots to a white screen when I hold "c," presumably because there is no OS on the hard disk.

Any insights?  Something I'm missing?  Remember I'm a complete beginner with Linux, so it may be something simple.  

Thanks,

Hot Pastrami

---

### Post by Krypton on 2005-08-04
[QUOTE=hot_pastrami]Good morning.  Sorry for the long post, but I want to detail everything I've tried:

I am attempting to install Hoary on a Dual G4 PPC, and running into a brick wall before I even get started.  The machine refuses to boot from the Ubuntu CD.  I'm a long-time Windows user, moderate-time OSX user, and first-time Linux user.

I downloaded the ISO from a mirror linked on ubuntulinux.org, and used Nero on a Windows XP box to burn it as an image to a CD.  The directories and files all appear to be there, and the disc is readable in OSX from my Combo drive.  There is also a dead Superdrive in this box, but as this system belongs to my employer, and given that I am inexperienced with Mac hardware, I am hesitant to open it and disconnect anything.

Initially, I tried inserting the CD and holding "c" while booting, but it still booted into OSX.  I tried booting and holding Option, and it displayed a screen with the Hard Disk and the Ubuntu CD (though it shows no label under the CD drive), but if I select the CD it just flickers the screen, and returns to the same menu.

I tried booting to Open Firmware, but the standard **boot cd:,\install\yaboot** failed, maybe because it's not the first CD device.  On a guess, I tried changing "cd" to "cd2," and then it showed some text too brifly to read, and stopped on a gray circle with a slash through it.

Just to be safe, I downloaded a new ISO onto the Mac, and burned it as an image using FireStarterFX, and repeated all of the above, with the same results.

As a last resort, I booted to OSX disc 1 and used the disk utility to wipe the hard drive, and replaced the HFS+ file system with UNIX File System (since I seem to remember reading that Linux doesn't get along with HFS+).  Rebooted, tried all of the above again, no change aside from the fact that it now boots to a white screen when I hold "c," presumably because there is no OS on the hard disk.

Any insights?  Something I'm missing?  Remember I'm a complete beginner with Linux, so it may be something simple.  

Thanks,

Hot Pastrami[/QUOTE]
 I find that the only way to get it to boot off of the disk is to shutdown with the CD in the Mac, then press the start button, then hold down 'C' immediately afterwards.

Otherwise it just boots up in OS X as you state.  (I'm new to Ubuntu!)

---

### Post by hot_pastrami on 2005-08-04
[QUOTE=Krypton]I find that the only way to get it to boot off of the disk is to shutdown with the CD in the Mac, then press the start button, then hold down 'C' immediately afterwards.

Otherwise it just boots up in OS X as you state.  (I'm new to Ubuntu!)[/QUOTE]
 Thanks for the reply... I've booted that way many times, with no success.  Any other ideas?

---

### Post by autocrosser on 2005-08-05
Well-take a look at the other post near yours--I think you don't have a "bootable" disc--seeing all the files is only part of the picture---take a look at-- [https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28ISO%29%7C%28burning%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28ISO%29%7C%28burning%29)

for more info--- You will be able to "C" key restart with a bootable in the drive--Macs have done it that way for over 10 years---If it won't=non-bootable disc--newer macs also have a open-firmware option--"Option" key on restart will allow a choice of every bootable on the system--this is only true for the "newer" macs--2000 & newer

Edit: I read your post closer--The Dead Superdrive is your problem--Is this a Mirror-Door with two slots for CD/DVD drives or are you trying to use a external drive? You can't boot off of an external--it needs to be the first CD/DVD device in the system. The Mirror-Doors use cable-select & always have the upper drive as master--the lower drive is slave.

---

### Post by hot_pastrami on 2005-08-05
[QUOTE=autocrosser]Well-take a look at the other post near yours--I think you don't have a "bootable" disc--seeing all the files is only part of the picture---take a look at-- [https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28ISO%29%7C%28burning%29](https://wiki.ubuntu.com/BurningIsoHowto?highlight=%28ISO%29%7C%28burning%29)

for more info--- You will be able to "C" key restart with a bootable in the drive--Macs have done it that way for over 10 years---If it won't=non-bootable disc--newer macs also have a open-firmware option--"Option" key on restart will allow a choice of every bootable on the system--this is only true for the "newer" macs--2000 & newer
[/QUOTE]
Yeah, I followed those instructions after my Nero burn failed, but it produced the same results.  If the ISO is for a bootable CD, then the CD burned from the image ought to be bootable, right?

[QUOTE=autocrosser]
Edit: I read your post closer--The Dead Superdrive is your problem--Is this a Mirror-Door with two slots for CD/DVD drives or are you trying to use a external drive? You can't boot off of an external--it needs to be the first CD/DVD device in the system. The Mirror-Doors use cable-select & always have the upper drive as master--the lower drive is slave.[/QUOTE]
It's a mirror-door built-in drive.  The only reason I don't think that the dead drive is the problem is because if I put OSX disc 1 in the secondary CD-ROM and hold "C," it WILL boot from it.  SO I know I CAN boot from that drive, given a proper bootable CD.

I am trying  a few other things, but maybe if I get desperate I'll open it up and swap the cable, making the good drive the primary CD drive.

Thanks,

Hot Pastrami

---

### Post by DJ_Max on 2005-08-05
[QUOTE=hot_pastrami]Yeah, I followed those instructions after my Nero burn failed, but it produced the same results.  If the ISO is for a bootable CD, then the CD burned from the image ought to be bootable, right?
[/QUOTE]
Not necessarily, a ISO is just a file. Can be used for other things. You have to make it bootable by burning the file as a "whole CD". Follow [these instructions](http://ubuntuppc.info/25.html) for Firestarter, or [try XCDRoast](http://ubuntuppc.info/58.html).

But, you may wanna check to see if you have a good ISO file. Verify the MD5SUM of the file.

---

### Post by hot_pastrami on 2005-08-05
[QUOTE=DJ_Max]Not necessarily, a ISO is just a file. Can be used for other things. You have to make it bootable by burning the file as a "whole CD". Follow [these instructions](http://ubuntuppc.info/25.html) for Firestarter, or [try XCDRoast](http://ubuntuppc.info/58.html).

But, you may wanna check to see if you have a good ISO file. Verify the MD5SUM of the file.[/QUOTE]
I wasn't just tossing the ISO on a CD, I was burning it as an image, so it *should* have worked.

I finally got it to install, though I can't say what did it... I unplugged the dead superdrive, reinstalled Panther on the G4, downloaded the Ubuntu ISO directly onto the Mac (I was downloading it on the PC before), and burned the image with FireStarterFX.  After all that, it booted to the Ubuntu install CD.

I may have a new problem... Ubuntu doesn't appear to be booting now that it's installed.  But if so, I'll do some hunting around, and post a new thread if I can't figure it out.

Thanks,

Hot Pastrami

---

### Post by autocrosser on 2005-08-05
When you unpluged the dead superdrive, you made the combo drive "master"-- Mirror-Doors used cable-select. A Non-Mac bootable has to be in the master--slave booting is not allowed--

See if you can get to your xorg.conf--You can reboot the install disc & "rescue" to be able to "see" the install in the drive-- Look for /etc/X11/xorg.conf & post it--Is the Mirror-Door using a Pro 9000 ATI??

---

