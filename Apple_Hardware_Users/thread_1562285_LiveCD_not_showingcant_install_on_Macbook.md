---
title: "LiveCD not showing/cant install on Macbook"
date: 2010-08-27
forum: Apple Hardware Users
---

### Post by adam_himself on 2010-08-27
Greetings my fellow Linux users!

Recently, I made the switch on my desktop to uBuntu and it was quite easy using Wubi to do a dual boot with Windows 7.  I decided to revitalize my old Macbook and bring it up to speed with uBuntu.  

I have another thread going, but I think the Apple Users forums might help me a bit more since I haven't been getting much of a response on my other thread (which I will close out).

My specs: Macbook, 3rd gen, 3.1, 1GB RAM, 2ghz Intel Core 2 Duo.

I made two LiveCDs.  One using Windows 7 disc imager and another using Infra Recorder.  First, when holding option key when booting with the LiveCD brings up my selection, but only for my HD and nothing else, not even the CD.  I have tried making a partition with Bootcamp, but it says something about volume, journal, or disc errors.  I checked, verified, and repaired my HD numerous times and I still get the error.  I tried my 2nd CD to see if it would recognize, this time it didn't error me, but reported the disc as being unwritten or blank.  I freaked when I saw this and put it in a 3rd windows machine I have access to... and low and behold the disc image was fine.  Everything was there...  So, Windows is reporting the CD as proper, but Mac is saying its blank?

I am trying not to completely reformat my system because I have lot of pictures and files on my Mac that I would like to save.  I am having backup problems with that as well (exporting from iPhoto), but that is a problem for another day.

A while back I even imaged a USB drive via uBuntu's directions on their site using Terminal and it wouldn't even recognize the USB when holding option.  

Here is the kicker... I repaired my Mac OS X installation this morning... and the Mac OS X CD was recognized then with no problem.  

I also installed rEFit and that works fine, but its not seeing the CD either... you can hear the CD drive running and working, but it never shows. And as soon as OS X starts it ejects my CD.

I am about to give up on Apple as a source of every day computing.  I find it trying too much to be "unique" and "main stream" while making it harder on people who want to do more than what they offer with their hardware.  Its like they took every possible good thing about Linux and made it a horrible bastard child who hordes everything to himself.

Anyways... to sum up... LiveCD not showing when holding option when I start.  The CD is showing fine and can be used to boot from a windows (bios) machine.  

(note: my previous thread can be found here: [http://ubuntuforums.org/showthread.php?t=1562208]("http://ubuntuforums.org/showthread.php?t=1562208") )

---

### Post by adam_himself on 2010-08-28
So... no help?

---

### Post by MChavero on 2010-08-28
> **adam_himself said:**
> So... no help?

Hi Adam,

I sounds like the ubuntu cd´s are not made properly since your MacBook can recognize the OS X Installation disc. Though the weird thing is that they work on a PC :S

Try downloading the ´Alternate CD´ and then burn it using Disk Utility on Mac OS X. If you haven´t use this version before, it is an installer without GUI, much more like the older Windows XP installer... The good thing is that they usually go very well installing the system with any kind of computer and sometimes even having weird issues like these.

Let me know if you haven´t use Disk Utility to burn ISO´s so I could tell you how. It´s something very simple (Like almost anything on Mac :D )

AND ALSO VERY IMPORTANT: Make sure you are using the same format as your OS X Installation disc (DVD´s?) It could also be a problem with the drive.

Regards.

---

### Post by gnat man on 2010-09-01
I am having the same problem, I have two Lucid Disks, one 10.04 and one 10.04.1, and neither one will boot on my Macbook 6,1.  I believe both were made with Ubuntu using Brasero.

They load up just fine on the PCs, but keep getting ejected on the Mac, both from startup, and when running OS X.

---

### Post by linuxopjemac on 2010-09-02
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

