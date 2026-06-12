---
title: "K3B Locking up PC..."
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-12-04
Hi all.
For the past few days, I havent been able to use K3B to burn ANYTRHING. See it starts quite fine. I tried creating an audio CD but it says it cant handle the file type (mime something error) yet w32codecs is installed, all gstreamer stuff is installed and I can play just about any file type. Ive even found a way to play mp3's with licence protection (WMPLAYER through WINE)...
Anyway, when I try to duplicate a disc, K3B opens up the dialog and alls well. As soon as I click start, my ENTIRE system freezes up, including the keyboard. I seriously have no idea why this happens, but I would appreciate some help. The same happens in root mode. Also, my image file is stored in the /media/data/images/, being an additional HDD where I stash all my media files. USER has all priveledges on the disk.

Please help..
B.

---

### Post by CaveRat on 2006-12-04
First of all, any burn ware uses a tremendous amount of system resources. This sounds very much like a hardware issue. You have not specified what resources you are working with. How much Ram do you have? What is the processing power? Are you running a CD-Rom and CD-burner simultaneously, or just a burner? Sometimes you have to compensate by doing one thing at a time. Baby steps. By this I mean run nothing else but the burn ware at the slowest speed such as 4X. Another thing I have had to do in the recent past is copy the desired disk to a folder in Home first. Then start K3B with nothing else running and burn from the folder at a slow speed. If these short steps still hang up the system, you might possibly have other issues to deal with.

---

### Post by online14230 on 2006-12-04
oops, sorry. Im running a Dell Optiplex GX 150, currently 512 MBSDRAM, 2 x 200GB HDD, Onboard graphics (Intel 815i) with 1 x Benq dw 1650 and an external cdrom (its a standard cdrom in a usb case). PS2 mouse and keyboard, with additional USB KB. Oh yeah, its a Piii. Ive shut the system down, started it up and go straight to K3B. As soon as It starts reading from the disc, it locks the system up. The only way to exit is to cut power.

Anything else?
Oh yeah, there are no errors listed when I dmesg |tail. The system was working fine until a few weeks ago. It was intermittent at first, but is now a 'permanent' thing.

Help?

edit: I tried using X-CDROAST also. It works fine, but I have to install proDVD. I searched for it, but cant find it. Any ideas? The only site that seems to have it is ftp.berlios.de

---

