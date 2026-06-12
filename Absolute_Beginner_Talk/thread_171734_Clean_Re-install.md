---
title: "Clean Re-install"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-07
I want to reformat the hard drive and install Ubuntu only instead of having a dual boot.  (Apparantly, it's done differently than rebooting with the install disc in the cd rom.)  I find it interesting that the book I bought 'Beginning Ubuntu Linux - From Novice to Professeional' not only doesn't tell you how to do this, but doesn't even tell you how to uninstall Ubuntu.  Curious, huh?  Anyway, can anyone tell me how I can do this, please?

---

### Post by confused57 on 2006-05-07
I may be wrong, but I think you can just select erase entire disk and install Ubuntu or select manual partitioning and set up the partitions how you want.  If you plan on saving lots of data files on your computer, you may consider putting /home on a separate partition.  That way, when you upgrade to dapper, you may want to do a fresh install of the final release and not risk losing your /home files.  If you want to do a separate /home, follow  herman's dual-booting guide for partitioning, for the screenshots & steps in doing this; but not actually setting up for dual-boot.   Since you're doing a fresh install anyway, you may want to give it a try.

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by Sef on 2006-05-07
Do you have a home partition or not?  If you do or not will change how to install.

---

### Post by Guns90 on 2006-05-07
Sorry it took so long for me to respond....church you  know.  

I guess I need to explain myself a little further.  I have already backed up all the files I want on a cd.  When I installed Ubuntu, I partitioned the hard drive 50/50 for windows and Ubuntu.  I now want to wipe everything off the hard drive and simply install Ubuntu.  

I think the problem I'm having now is that the hard drive is being read before the cd rom.  Prior to installing Ubuntu, I could access the CMOS settings (I think that's what they are called) by pressing Alt and F2 and change the order of devices.  By my way of thinking (imagine that), I believe that I need to access the cd rom drive before the hard drive so that the autorun program on the Ubuntu install disk will be read.  I think that then I will be able to reformat the hard drive and do a fresh install.

---

### Post by mips on 2006-05-07
Yes, go into bios and configure to boot from cd first.

---

### Post by confused57 on 2006-05-07
mips is right, you'll still be able to select the cd drive to boot first in bios regardless of the operating systems you have installed.

It would definitely be easiest to do the erase entire disk and install Ubuntu.  Later, you may want to try re-installing doing the manual partitioning with separate /home.

---

### Post by Guns90 on 2006-05-07
I guess I didn't explain my problem very well in the last post.  I don't know how to get into BIOS now.  That is what I need help with (assuming that, if I can access the Ubuntu install disk, I will be able to reformat the hard drive.  If I can't reformat the hard drive using the install disk, I need to know that).

---

### Post by uzi09 on 2006-05-07
you will be able to format hdd using the install cd. here is a great guide to installing ubuntu (including if u want to create a seperate /home partition):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

to get into the bios is a little hard for us to explain because there are so many different ways companies have it setup. the best thing u can do, is look very very closely (get a buddy to help if u need) what the first few lines of text say when you boot up the computer. it's usually just one key that'll do the trick for you. if u still can't catch it, just try some of the popular keys:

F2, F8, F12, DEL

just press it repeatedly as you boot up the computer, it'll *hopefully* get you into the bios

let us know what you come up with. also, if you can tell us what type of computer you have, someone may also have the exact same one and could probably let you know exactly what to press to get into your bios.

---

### Post by Guns90 on 2006-05-07
[QUOTE=uzi09] if you can tell us what type of computer you have, someone may also have the exact same one and could probably let you know exactly what to press to get into your bios.[/QUOTE]

Sorry guys, I see now that I should have told you what my hardware is.  I have a generic computer with an ASUS A7N7XE-Deluxe, Athlon XP 2500+, Radeon 9200, and Western Digital HD.  I guess somehow I changed the BIOS to boot in the order it currently is.  It says right on the first screen to use  ALT F2 to enter BIOS, but that isn't working now.  The GRUB program is taking control first.  I'm going to reboot now and try the ones you suggested.  I'll be back one way or the other.

---

### Post by confused57 on 2006-05-07
If that doesn't work, you may need to just hold down the "Alt + F2" keys or the keys suggested, as soon as possible during bootup.

Grub is booting from your hd, so I don't think it can start before you have the option of entering the bios setup, the bios pretty much has to do a self-test before your computer can bootup.  Usually it's a timing thing, may take several attempts to get the timing just right during bootup to enter bios.  It may involve just hitting the necessary key(s) or holding them down, usually as soon as you see any kind of display during startup.

---

### Post by jorn on 2006-05-07
Often it's displayed on the screen what tap to press for getting into Bios.
If it disappears to quickly try pressing the Pause/break tap.

---

### Post by Guns90 on 2006-05-07
Well guys, I sure appreciate all the responses.  As you can see, I'm back up.  This time it's with Ubuntu only.  

I have no idea what I did to mess things up.  I guess I'll learn stuff like that as time goes by.  FYI, I knew that my BIOD could be accessed with the ALT F2 buttons, it's written right on the start up page for my motherboard; however, they weren't working.  I tried the others listed above and the 'DEL' did the trick.  Again, thanks for the responses.  See ya'll around I'm sure.

---

