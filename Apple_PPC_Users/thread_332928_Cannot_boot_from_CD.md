---
title: "Cannot boot from CD"
date: 2007-01-06
forum: Apple PPC Users
---

### Post by don skoog on 2007-01-06
I'm on an IMac OSX 10.4.8. I've downloaded Ubuntu 6.06.1 powerpc and verified it in Disk Utility, but when I restart I get OSX instead of Ubnuntu. I've tried starting while holding the "c" and also the "option" button. But it won't boot up.

Any ideas?

Don

---

### Post by xiaoxin on 2007-01-06
I have no experience with macs what so ever.
But i would say set the bios to boot from cd first.

---

### Post by linear on 2007-01-06
Some iMacs are very finicky about bootable CDs. You didn't say what vintage iMac. The iMac is not recognizing the CD as bootable.

1. Sure it was burned as an image?
2. Burned at a slow speed (4x or less)?
3. Have you tried the alternate install disk?

---

### Post by 3rdalbum on 2007-01-07
Does the contents of the CD appear when you insert it into your iMac while OS X is running?

If not, then it's probably too fast a burn speed. If the drive sounds like it's struggling to read the disc, then try burning onto a disc that is designed for music.

If the disc reads, and all that's on there is one file, then you need to burn the file as a disc image (but you sound smart enough to have already realised this).

---

### Post by handylinux on 2007-01-07
I've downloaded and used only the 6.10 PowerPC CD and it's worked fine, so I'm not sure what your problem is, but here are a few thoughts:

> I've downloaded Ubuntu 6.06.1 powerpc and verified it in Disk Utility, but when I restart I get OSX instead of Ubnuntu.
When I asked Disk Utility to "Verify" my Ubuntu CD, it failed with an error message: "The underlying task reported failure on exit." "Invalid number of allocation blocks." etc. Maybe the CD is bad, but like I said, it's worked fine, so I suspect this is because Disk Utility doesn't recognize its file system. Get Info says it's a "Mac OS Standard" volume; I'm not sure if this is correct, but if Get Info tells you your CD is "Mac OS Extended" then it's probably been burned incorrectly.

If Disk Utility told you your CD was fine, it may be you just copied the .iso file to a CD (which would be in Mac OS Extended format), which won't work. The .iso file is the PC version of a Mac .dmg file; you have to use Disk Utility's Burn command (under the Image menu) to make a clone of it to a CD.

> I've tried starting while holding the "c" and also the "option" button. But it won't boot up.
What did you see when you pressed option during startup? If you saw a hard disk icon with a penguin, you should be able to start from it. If you saw only a hard disk icon with an X, your CD isn't bootable.

> But i would say set the bios to boot from cd first.
The Mac version of this is to to use the Startup Disk preference pane to set a different startup system, but it won't work in this case as Mac OS X doesn't recognize Linux as a bootable System.

When you insert the CD while running Mac OS X, does it appear on the desktop? Does it have a name? e.g. mine is "Ubuntu_PowerPC_edgy". If it's "untitled" it wasn't burned correctly; you probably just copied the .iso file to it.

Do you have another bootable CD, e.g. a Mac OS X Install disc? Try that to verify the drive. If it works, then your problem is almost certainly your Ubuntu CD, which could be either incorrectly created (e.g. a Finder copy rather than a clone from the .iso file) or simply a faulty burn (bad CD, etc.).

---

### Post by don skoog on 2007-01-07
Thanks for all the suggestions,

You were right, I didn't have it burned as a .dmg file.

So I burned a new one from the Images icon on disk utility. The new one verifies and is recognized in the finder but I still cannot boot it from either "x" or "option" on startup and the Starup disk function in Preferences doesn't recognize it. I'm stumped.

Open to suggestions but out of ideas.

Don

---

### Post by handylinux on 2007-01-07
> **don skoog said:**
> The new one verifies and is recognized in the finder but I still cannot boot it from either "x" or "option" on startup and the Starup disk function in Preferences doesn't recognize it. I'm stumped.
I'm sorry, but you aren't providing enough information for anyone to help you. If you could take the trouble to answer the questions in my previous post, maybe we could get somewhere. I repeat:

Startup Disk in System Preferences doesn't recognize it because it isn't a Macintosh System. It will never recognize a Linux volume (CD, HD, whatever) as bootable.

When you insert the CD while running Mac OS X, does it appear on the desktop? Does it have a name? e.g. mine is "Ubuntu_PowerPC_edgy".

What did you see when you pressed option during startup? If you saw a hard disk icon with a penguin (in addition to a hard disk with an X), that represents the CD, and you should be able to start from it. If you saw only a hard disk icon with an X, your CD isn't bootable.

Do you have another bootable CD, e.g. a Mac OS X Install disc? Try that to verify the drive.

---

### Post by don skoog on 2007-01-07
Sorry for not being clearer. Yes, when I load the CD in OSX it comes up on the finder as "Ubuntu Mac" which is what I named it.

When I double click the CD it shows an Ubuntu .dmg file.

When I start up holding the option key there is no penguin icon.

I am now downloading the alternate CD but will try my OSX startup CD as soon as it's finished.

Don

---

### Post by linear on 2007-01-07
> **don skoog said:**
> Sorry for not being clearer. Yes, when I load the CD in OSX it comes up on the finder as "Ubuntu Mac" which is what I named it.

When I double click the CD it shows an Ubuntu .dmg file.

That's an important clue - if you were able to name it, then you did not burn the .iso file as an image. You must burn as an image to get a bootable CD.

---

### Post by handylinux on 2007-01-07
> **don skoog said:**
> Sorry for not being clearer. Yes, when I load the CD in OSX it comes up on the finder as "Ubuntu Mac" which is what I named it.
If you made the CD correctly, you wouldn't have named it; it already has a name. Since you're using (as I recall) a 6.06 CD I don't know exactly what that would be, but probably something like "Ubuntu_PowerPC_dapper". (Why are you using 6.06 instead of 6.10, BTW?)

> When I double click the CD it shows an Ubuntu .dmg file.
I suspect you still haven't made a proper CD. It sounds like you somehow converted the .iso file you downloaded into a .dmg file, then copied that onto a CD? You should not see an "Ubuntu .dmg file" anywhere. 

> When I start up holding the option key there is no penguin icon.
Because there isn't a bootable Linux CD.

How to make the bootable Ubuntu CD:

1) Open Disk Utility.
2) Drag the "ubuntu-6.06.1-desktop-powerpc.iso" disk image (I believe that's the name the file has after you download it) to the area in the left side of the Disk Utility window; it should then appear there as a little icon under the icon representing your hard disk.
3) Select the "ubuntu-6.06.1-desktop-powerpc.iso" icon there in Disk Utility by clicking on it once.
4) Under Disk Utility's "Image" menu, select "Burn..."
5) Insert a recordable CD as prompted, and tell it to burn at 4x (a slow speed to make sure the burn is accurate).
6) When you follow this procedure, there is no way for you to name the CD; it ends up named the same as the CD from which the .iso image was made.

For instance, I've downloaded a CD image for the alpha of the upcoming Ubuntu release. The image file's name is "feisty-desktop-i386.iso". When I double-click it, it mounts as if it were a disk, and has the name "Ubuntu 7.04 i386", which is the name that would appear on a CD made from it.

To see what your CD should be named, double-click the .iso file to mount it; the name it has when it appears on your desktop is the name a CD burned from it should have.

For more on disk images and working with them, open Disk Utility's Help.

So far as I can tell, it looks like your problem is that you haven't yet made a proper CD from the downloaded disk image. You cannot simply copy the CD image file onto a CD, as if you were backing up a file; and neither can you mount the image and copy the files from it onto a CD; you have to use Disk Utility to make a CD out of the image. When you do that, the new CD is an exact copy, bit-for-bit, of the original CD from which the image file was made. That's what you want.

---

### Post by don skoog on 2007-01-08
Handylinux!

Thank you for your patience and your idiot-proof directions. Ubuntu booted from the disk. Of course, it froze a little while later, but I'm chalking that up to my relying on the disk instead of installing it.

I'm going to try and create a disk that will work on my Windows machine (don't laugh, it was free, and it needs Ubuntu way more than my Mac does.)

I'm sure I'll be back with more stupid questions later- your cross to bear being so good at explaining things to newbies- but until then, thanks again,

Don

---

### Post by gurnemanz on 2007-01-08
> **handylinux said:**
> You cannot simply copy the CD image file onto a CD, as if you were backing up a file; and neither can you mount the image and copy the files from it onto a CD; you have to use Disk Utility to make a CD out of the image. When you do that, the new CD is an exact copy, bit-for-bit, of the original CD from which the image file was made. That's what you want.

](*,) 

Mayhapply this could be made a sticky for those of us with more willingness than experience!

Gordamuckty! The hours I might have saved, and now have saved! Thank you, handylinux!

g.

---

### Post by handylinux on 2007-01-08
> **don skoog said:**
> I'm going to try and create a disk that will work on my Windows machine (don't laugh, it was free, and it needs Ubuntu way more than my Mac does.)
Yeah, it's in the PC world that Linux is really needed; for a Mac it's more of a curiosity. I'm hoping to come into a free PC myself (would be my first after 18 years of Macs) to begin learning Linux on it.

Another tip: If you're planning to keep both Ubuntu and Mac OS X on your Mac for dual booting, it'll be more convenient if you **install Ubuntu on the first partition**. See **[this post]("http://www.ubuntuforums.org/showthread.php?p=1951103#post1951103")** for some details.

---

