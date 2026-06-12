---
title: "Burnt CD not working"
date: 2004-10-23
forum: Apple PPC Users
---

### Post by kadymae on 2004-10-23
So, I decided to throw Ubuntu on a Apple Powerbook I have lying about.

2000 G3 500 Pismo with 512mb ram

I downloaded ppc iso, dragged it to my blank CD and burnt.  

I popped into my laptop, rebooted while holding down the C key, and the drive spins up, but after about 30 seconds, I'm booting into OS 9.

To make sure that it wasn't a problem with my drive, I've just slapped in my OS X disk, rebooted with the C key down, and I'm now looking at an OS X installer screen. So clearly, all is hunky dory with my disk drive.

Is there something I need to do to the iso before I burn it?  Any clues on why this disks I burn (and I burned yet another on a different computer, fresh download and all) will not mount to an install screen?

The instructions at Ubuntu say download the ISO, burn, hold down C and the installer will start.

I also notice that there's other PPC files at the download page.  What do they do?  Do I need them?  Does my ISO need to be "unpacked" somehow before burning?

---

### Post by im_ka on 2004-10-23
make sure you do an md5sum check before you burn the .iso image. also, burn the cd with a low speed (8x). the faster you burn it, the greater the chance of an error.

hope this helps

---

### Post by Rancoras on 2004-10-23
Did you burn the actual iso file to the disc?  If your disc only has one file on it, then you did it wrong.  If it's right, it will have several folders and files on it.  You need to make sure you are burning the image.  If you're doing this on a MAC, I have no idea what you would use.  Toast maybe?

---

### Post by kadymae on 2004-10-23
[QUOTE=Rancoras]Did you burn the actual iso file to the disc?  If your disc only has one file on it, then you did it wrong.  If it's right, it will have several folders and files on it.  You need to make sure you are burning the image.  If you're doing this on a MAC, I have no idea what you would use.  Toast maybe?[/QUOTE]

Okay, I followed the instructions here:

[http://www.ubuntulinux.org/support/documentation/howto/installation-powerpc/view?searchterm=how%20to%20install](http://www.ubuntulinux.org/support/documentation/howto/installation-powerpc/view?searchterm=how%20to%20install)

I downloaded a file called warty-powerpc.iso and burnt it to a CD via a drag and drop on my Powermac.  It doesn't work.  Since 500+mb represents 1/3 of my monthly bandwidth at home, I downloaded again at work and burnt that via a drag and drop on a workstation running XP pro.

Each time I ended up with ONE file on my CD.

Where do the extra files and folders come from?

[edited to add]

Thanks!

---

### Post by Rancoras on 2004-10-23
Google for burn iso image osx yielded this:

1) Run the Applications:Utilities:Disk Copy application
2) Select "File...Burn Image..."
3) Dialog pops up allowing you to select the ISO image
4) Dialog pops up with a "Burn" button on it (assuming media is ready)
5) Burn that baby!

Since I don't own a mac, I cannot test this for accuracy but it may point you in the right direction.

---

### Post by ericc on 2004-10-26
[QUOTE=Rancoras]Google for burn iso image osx yielded this:

1) Run the Applications:Utilities:Disk Copy application
2) Select "File...Burn Image..."
3) Dialog pops up allowing you to select the ISO image
4) Dialog pops up with a "Burn" button on it (assuming media is ready)
5) Burn that baby!

Since I don't own a mac, I cannot test this for accuracy but it may point you in the right direction.[/QUOTE]

Hello guys,
I got the same problem, can't burn a bootable CD. I use Disk utility in that way and it crashed every time I try to open the iso image. I did that way for several other distros and had no problem. I also downloaded it several times in YDL, MacOSX, with curl, bittorrent,  firefox ... and never succeed burning a bootable CD !
Any Idea ? Did anyone overthere succeed ?
Regards,

---

### Post by Ptero-4 on 2004-10-26
[QUOTE=ericc]Hello guys,
I got the same problem, can't burn a bootable CD. I use Disk utility in that way and it crashed every time I try to open the iso image. I did that way for several other distros and had no problem. I also downloaded it several times in YDL, MacOSX, with curl, bittorrent,  firefox ... and never succeed burning a bootable CD !
Any Idea ? Did anyone overthere succeed ?
Regards,[/QUOTE]
The warty iso crashing Disk utility is a known problem with the 4.10 rc1 iso, it was fixed in the 4.10 final release iso.

---

### Post by Ptero-4 on 2004-10-26
[QUOTE=kadymae]So, I decided to throw Ubuntu on a Apple Powerbook I have lying about.

2000 G3 500 Pismo with 512mb ram

I downloaded ppc iso, dragged it to my blank CD and burnt.  

I popped into my laptop, rebooted while holding down the C key, and the drive spins up, but after about 30 seconds, I'm booting into OS 9.

To make sure that it wasn't a problem with my drive, I've just slapped in my OS X disk, rebooted with the C key down, and I'm now looking at an OS X installer screen. So clearly, all is hunky dory with my disk drive.

Is there something I need to do to the iso before I burn it?  Any clues on why this disks I burn (and I burned yet another on a different computer, fresh download and all) will not mount to an install screen?

The instructions at Ubuntu say download the ISO, burn, hold down C and the installer will start.

I also notice that there's other PPC files at the download page.  What do they do?  Do I need them?  Does my ISO need to be "unpacked" somehow before burning?[/QUOTE]

Your problem is that you are probably trying to boot an oldWorld Mac with yaboot.
To boot oldWorld Macs you need to install the BootX control panel in OS9 , slap your Ubuntu CD in your drive, reboot and (hopefully) select your CD from the BootX menu.

P.D: I don´t have any oldWorld Mac to test it out but I read it in an old YellowDog Linux support article.

---

### Post by kadymae on 2004-10-29
Ptero-4  the Pismo is not an "old world" mac.

The way to tell an "old world' mac from a "new world" mac is simple:  did it come with built in USB ports?

If yes, it's new world.

---

### Post by kadymae on 2004-10-29
[QUOTE=Rancoras]Google for burn iso image osx yielded this:

1) Run the Applications:Utilities:Disk Copy application
2) Select "File...Burn Image..."
3) Dialog pops up allowing you to select the ISO image
4) Dialog pops up with a "Burn" button on it (assuming media is ready)
5) Burn that baby!

Since I don't own a mac, I cannot test this for accuracy but it may point you in the right direction.[/QUOTE]

sorry to be so late on getting back to you (nasty bout of food poisoning kept me down) but under OS X 10.3.x there is **nothing** called "disk copy" under the Utilities folder.  

I'm going to try the disk utility and see if that has something I can use.

---

### Post by DaveyJJ on 2004-10-29
[QUOTE=kadymae]sorry to be so late on getting back to you (nasty bout of food poisoning kept me down) but under OS X 10.3.x there is **nothing** called "disk copy" under the Utilities folder.  

I'm going to try the disk utility and see if that has something I can use.[/QUOTE]

In 10.3.x the "Disk Copy" functionality and a bit more was rolled into a new "Disk Utility" package.

But since I also can't get the CD to be bootable ...  :sad:

---

