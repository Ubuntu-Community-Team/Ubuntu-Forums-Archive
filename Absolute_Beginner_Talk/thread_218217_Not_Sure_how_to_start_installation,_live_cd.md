---
title: "Not Sure how to start installation, live cd?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by greyham on 2006-07-18
Hi

Im really new to this so if something that i say is completely noobish, sorry:( . Anyway yesterday i downloaded the Amd64 disc (think it was a liveCD)of Ubuntu 6.06 i had a look around it but i cant open anything (well apart from .txt and 3 pictures). Please help me as i would love to try Ubuntu out even if i have used windows for my whole life

Thanx Greyham:D

---

### Post by ovimunt on 2006-07-18
Hi,

Are you trying to open it from Windows? 

You're actually supposed to boot from it. So put it in the drive, restart and make sure the computer boots from the CD.

*EDIT:* After you boot from the CD you can choose to start up Ubuntu in graphic mode and install from there or to install in text mode instead. 

I personaly prefer installing in text mode but either way you have to be very careful when you reach the point of choosing the partition you want to install to.

For Ubuntu, as a minimum, you would need either about say 5GB of unalocated space on your HDD or as a different partition or two separate partitions of say 4.5GB and 512MB. One would be used as the root partition (main linux partition) and the other as SWAP space. The SWAP partition is optional but it is advisable to use one.

VERY IMPORTANT: Make sure you don't choose one of your in use existing partitions to install Ubuntu on! If you format them you will loose all the data!

---

### Post by fatsheep on 2006-07-18
There should be an installer shortcut on the desktop, double click on it.  

However, I warn you: there are problems with the Live CD installer.  I would recommend going with the alternate CD installer if you have problems with the Live CD install.  

Good luck with Ubuntu,

-sheep

---

### Post by T700 on 2006-07-18
First, make sure you downloaded the correct version.  Are you running a 64bit AMD chip?  Also, be certain you downloaded the desktop install--not the server.

Next, you need to burn the ISO image.  What you downloaded is useless, by itself.  You have to use CD burning software (Nero, etc.) to *burn the ISO as an image.*  **Do not** copy it to the CD and **do not** make a bootable disk; neither will work.

Lastly, make sure your PC is set to allow booting from the CD drive.  Most are, but if not, you will have to make a very simple adjustment in the BIOS.  If this is the case, post back and we'll help you.  Otherwise, pop the CD in, reboot, and enjoy Ubuntu!  When you're done, take the CD out, reboot, and you're back to Windows.

Good luck and welcome,
Paul

---

### Post by greyham on 2006-07-18
thanx for the such quick replies:-D 
ok well i tried twice to boot from the CD but T700 your probobaly right about that.:-D 
Also thanks to ovimunt for originaly telling me too boot from cd i wasn't sure if i was meant to.:) 
and fatsheep i don't have any shortcuts on the desktop:confused:
and if it does help im running vista beta 5384
Greyham

---

### Post by greyham on 2006-07-18
um i have a AMD Athlon 64 3200+ so is that the 64 bit one?

Thanx Greyham

---

### Post by Sef on 2006-07-18
> um i have a AMD Athlon 64 3200+ so is that the 64 bit one?
[QUOTE]i downloaded the Amd64 disc (think it was a liveCD)of Ubuntu 6.06 [/QUOTE]

Yes it is.

---

### Post by Metacarpal on 2006-07-18
> **greyham said:**
> ... i don't have any shortcuts on the desktop:confused:
and if it does help im running vista beta 5384
Greyham

When you get the LiveCD booted up, there will be an installation icon on the Ubuntu desktop. :) You can look around in Ubuntu without installing.  (note: it will be noticably faster if you install to desktop, so don't worry if the LiveCD seems a little slow).

If you like what you see, then you can just double-click the icon on the Ubuntu desktop to start installing to your computer.  Keep the tips from Ovimunt and T700 in mind!

---

### Post by mattisking on 2006-07-19
> **greyham said:**
> thanx for the such quick replies:-D 
ok well i tried twice to boot from the CD but T700 your probobaly right about that.:-D 
Also thanks to ovimunt for originaly telling me too boot from cd i wasn't sure if i was meant to.:) 
and fatsheep i don't have any shortcuts on the desktop:confused:
and if it does help im running vista beta 5384
Greyham

Greyham, Please excuse me if this sounds like I'm talking down to you in any way. When you booted from the CD, did it boot into Gnome or into Windows Vista? If it booted Windows Vista, did you pay attention while it booted? There was a point where it should have asked you whether or not to boot from the CD (depends on the BIOS). If you were never prompted and it booted straight to Windows, then one of two things have happened:
1) The Ubuntu Dapper Installation CD either was messed up during the download or when you burned it to CD. In this case, try re-downloading.
2) If you're pretty sure the CD is ok, go into your BIOS and make sure that your first bootable device is your CD and not your harddrive.

---

### Post by greyham on 2006-07-23
Hi 

thanx for everyones replies i did re-download the iso and re-burn it and when i  loaded it into windows a window popped up with some programs that work with ubuntu and windows and saying to boot with the cd. I tried this but it just loaded straight back into windows. I am not sure exactly how to change the BIOS so can someone help?

Thanx again,Greyham:)

---

### Post by _simon_ on 2006-07-23
ok, restart your machine. You will see at the bottom (normally of the very first black screen, sometimes second) that it says to press a key to enter BIOS, normally this is DEL

Once in bios you need to find the screen that has boot order. 

Depending on what drives you have you'll want something like:

Floppy
CD
Harddrive

or if you don't have a floppy just

CD 
Harddrive

The boot sequence uses drive letters so you need to know what letters your drives are 

e.g.

A
D
C

Once you have it booting from CD first, save settings and exit, now when you boot with the CD in, it should either automatically boot straight to CD or give you a timed option to boot to CD or if you don't make a choice then straight to Harddrive

On another note, you say you have vista installed... if you have it for eyecandy then you'll be pleased to know that with XGL & Compiz (read up on it when you are comfortable with using Linux) you can have more eye candy than Vista - you can even make Ubuntu look like vista - link to my vista inspired ubuntu [Clicky](http://i17.photobucket.com/albums/b96/snewberry1980/Screenshots/vistastyle.png))

---

