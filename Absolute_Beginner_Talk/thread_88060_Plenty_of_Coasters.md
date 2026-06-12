---
title: "Plenty of Coasters"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Smandola on 2005-11-09
Please excuse my ignorance if this has been a covered topic.  I am a newbie to Ubuntu, and linux.  However, I am having difficulty getting a CD with a proper image.  Firstly, here are the steps that I have gone through:

1) Downloaded "ubuntu-5.10-install-i386.iso" using Bittorrent
2) Ran MD5 Check Sum, the numbers match, so I got a good download of the ISO file.
3) Used Roxio, on a win xp pc to burn the Image.  I followed the steps to "Record CD from Image", and I selected the .iso image file.

Result = Coaster.


Ok, so here are my variations:
A) Downloaded using ftp & Steps 2 & 3, result = Coaster
B) Used steps above on a different pc with different version of Roxio, result = coaster
C) Tried burning at different speeds (ie: 4x, 2x), on different pc's, results = coasters (yes plural)
D) even tried K3B from a different linux distro, result = coaster. (this one could be my lack of knowledge with K3B).

Also, note that I have downloaded a different distro of Linux and been able to burn images previously, so I'm not a complete dork that way.  The other linux distro ISO and subsequent CD work just fine.  So I don't think its a hardware issue.  
I'm very methodical, hence I think that I would have been able to figure this out on my own... but I'm at a loss as to why my CD's are turning into Coasters.  

All of the CD's look the same once burnt.  The Directory/file structure is as follows: 
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=3455&stc=1&d=1131558147[/IMG]

So I do have files and directories on the CD, but I don't know if this is correct or not.  I'm assuming that if you have the .iso file on the CD that would be bad. 

Any help or redirection towards another thread would be greatly appreciated.
Thanks in Advance.

---

### Post by scflymedic on 2005-11-09
CDBurnerXP Pro, [www.cdburnerxp.se](www.cdburnerxp.se).  I've burned many ISOs without coasters and best of all it's free

---

### Post by jasay on 2005-11-09
What about the cd's exactly makes them coasters?  They don't boot?  Don't run the install?  As you said they certainly appear to have files and folders on the them.  Checking your screenshot against my install cd, they look the same.

---

### Post by Smandola on 2005-11-09
[QUOTE=jasay]What about the cd's exactly makes them coasters?  They don't boot?  Don't run the install?  As you said they certainly appear to have files and folders on the them.  Checking your screenshot against my install cd, they look the same.[/QUOTE]

When I put the CD into the pc (the one that I want to load Ubuntu on) the CD is unrecognized.  The same holds true for any other pc that I put the CD into... it doesn't recognize the CD (and any of the other coasters).

---

### Post by steve.horsley on 2005-11-09
[QUOTE=Smandola]When I put the CD into the pc (the one that I want to load Ubuntu on) the CD is unrecognized.  The same holds true for any other pc that I put the CD into... it doesn't recognize the CD (and any of the other coasters).[/QUOTE]

Thet's not making sense. If it's not recognised as a CD, how did you get the screen shot of its contents?

I've used Nero under windows. It has a menu option for burning a CD from an image. Note that **image** is the important word here.

---

### Post by froggybugs on 2005-11-09
This sounds like almost the exact problem I'm having. I don't have a solution, but you might want to take a look at the thread I started in the Installation forum ([http://ubuntuforums.org/showthread.php?t=88059](http://ubuntuforums.org/showthread.php?t=88059)) WinXP Roxio won't burn ISO.

---

### Post by raublekick on 2005-11-09
try selecting the "finalize" option?

---

### Post by chazzjazz on 2005-11-09
MAKE sure you burn the image, and not create a new disc. burning an iso image finalises it immediately

to check the iso, just double click the drive and it should pop-up asking you what option to do, play with player, open etc

innero it will ask for a file with extension iso, nrg, or cue

---

### Post by cbudden on 2005-11-09
Do you have the BIOS set to boot from the CD before the hard drive?

---

### Post by ssam on 2005-11-09
it looks like you are doing the burning process right.

have you checked that the bios is set to boot from cd? usually you press del or f1 or something like that at boot to get the bios options. somewhere in there you can choose the boot order. for example: floppy, cd, 1st hard disk. that will try those drives in that order looking for something bootable. if the hard disk is set before the cdrom, then it will ignor that you put a disk in.

will any other cd boot? eg other linux install/live disks, or the windows install disk. could you download [damn small linux]("http://www.damnsmalllinux.org/") and see if that boots.

---

