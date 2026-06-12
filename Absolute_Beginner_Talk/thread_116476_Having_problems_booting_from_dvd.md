---
title: "Having problems booting from dvd"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by berherpman on 2006-01-12
Well, I'm new to Linux and new to this forum, and hope I'm not posting a stupid question, but I've been searching for a little while and can't seem to find the solution to my problem :( .  I've downloaded the ISO file and burned it to a dvd.  My computer boots up from the dvd fine, and I get the ubuntu screen, but when I try to run live dvd or even install it I get an "Invalid or corrupt kernel image" error.  I'm not using a mac, and am not running 64 bit, and am 99% sure I've got the right ISO file.  I really want to get into Linux, and hope someone can help me before I give up.  Thanks in advance!

---

### Post by SavageBeginner on 2006-01-12
It's probably corrupt data. Either the DVD burn is bad, or the ISO file is corrupt. I'd try re-burning the DVD slowly (2x), try again, and if that doesn't work download the ISO again.

---

### Post by StefanoCole on 2006-01-13
Also, after you have downloaded the iso file check the MD5 checksum of it. Just to be sure the image has been downloaded without any corruption.

Stefano

---

### Post by AMD64_N_Linux on 2006-01-13
New to Linux ? Then I would guess that you downloaded your ISO in windows and are using Windows to burn the ISO. You will need to grab a couple of things from the internet.

First go back to where you downloaded the ISO. There will be a file called MD5SUMS in the same directory as ISO file(s) It is a text file without the .txt extension.
Put that file in the same directory as the ISO file.

Next download one of these

My personal choice...
w/GUI

[http://www.md5summer.org/download.html]("http://www.md5summer.org/download.html")  

or another
w/Command line

[http://www.slavasoft.com/fsum/]("http://www.slavasoft.com/fsum/")

check the md5sum against the ISO.

If you are using the command line tool, the command should be

open a command prompt window
assuming the Folder is C:\Ubuntu type these commands 

cd ..
cd Ubuntu
fsum.exe -c MD5SUM

Fsum will check that the md5sum of the ISO is correct (the ISO is not corrupted ) 

Now you see why I prefer MD5Summer, anyway,,,,

When you burn the ISO, do it a less than maximum burn speed. If you have a 16x burner, run it at 8x MAX. If it is an 8X, use 4X max.

This insures a cleaner burn.

Reboot your machine with the DVD in the drive,,,,

Welcome to Linux....

---

