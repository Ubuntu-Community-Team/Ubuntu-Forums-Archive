---
title: "Ubuntu 6.06 Installation Error"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by FFfanatic on 2006-11-05
I've downloaded an burnt the iso for Ubuntu 6.06 to a CD, then booted from the CD. Near the beginning, it says that the mouse driver is installed either successfully or unsuccessfully (it doesn't matter in the end I think), but then it waits at

A:\

for me to enter something, can anyone help me with what I'm doing wrong?

---

### Post by teet on 2006-11-05
> **FFfanatic said:**
> I've downloaded an burnt the iso for Ubuntu 6.06 to a CD, then booted from the CD. Near the beginning, it says that the mouse driver is installed either successfully or unsuccessfully (it doesn't matter in the end I think), but then it waits at

A:\

for me to enter something, can anyone help me with what I'm doing wrong?

Sounds like you have a floppy disk in your floppy drive.

Eject the floppy disk from your floppy drive and try again.

Also, make sure your BIOS is set to boot from a CD.

-teet

---

### Post by David_T on 2006-11-05
So you made sure that in the BIOS it was set to boot from CD?
Do you ever see anything on your screen related to Ubuntu (like the live CD menu)?  If so which option did you choose?

---

### Post by .t. on 2006-11-05
Yeah, that's a DOS prompt, not any kind of UNIX.

---

### Post by FFfanatic on 2006-11-05
There is no floppy in the drive.
To set bios, I press Del before boot and in the Advanced BIOS Menu, I change it to boot from my CD drive.

I never did see anything relating to Ubuntu as I rebooted after changing the BIOS.

Is it possible that Ubuntu doesn't want to dual boot with Windows for some reason?

And lastly, is there any specific program you used to make a bootable CD? I used NTI CD&DVD Maker 7 Gold, which gives you the option to make a bootable CD or DVD. Is it possible that I missed a file when I copied them to CD?

My process for burning was:
 - downloaded the 698MB zip.
 - extracted files
 - copied files and pasted into folder
 - opened folder in NTI
 - checked box to make it a bootable CD
 - burnt CD

One more thing, where is the iso if it is included in the zip file? Because when I burn the CD, it asks me if I want to burn from the current iso image. Just wondering if I should choose a specific file.

---

### Post by LLRNR on 2006-11-05
Hi FFfanatic ! You said in your first post :
[quote="FFfanatic"]I've downloaded an burnt the iso for Ubuntu 6.06 to a CD, then booted from the CD[/quote]
ok, so you got an iso. But in your second post, you say that
[quote="FFfanatic"]downloaded the 698MB zip[/quote]
Alright, I really don't understand wether you downloaded an ISO file or a ZIP file. I also got at download a 698 MB ISO file...
_Suppose you got an ISO :_ You don't need to extract it, you only need a CD burner that supports ISO burning (I for instance used Nero). And to me the "Make bootable CD" option sounds a little bit strange. We don't need to make it bootable from the CD burner program since we change the boot order from BIOS and make it boot from the CD. I also get this choice using Nero but I didn't even think of using it... my CD blank is much too precious for that. I don't know if NTI supports iso burning, I never tried it myself, but I guess any serious burning tool should support iso burning.
_Suppose you got a ZIP :_ Alright, you must un-zip it, and then burn the un-zipped files normally to a CD (again, without enabling the "Make Bootable CD" option).

Second thing to do is insert the CD, reboot and change the boot order from BIOS (it depends on your BIOS how to do that, but you already managed to do it as far as I understand). After this procedure, the freshly-burnt CD should boot with no problems and you should be ready to install Ubuntu...

Good luck !

LLRNR

---

### Post by FFfanatic on 2006-11-05
My mistake at the beginning, sorry to all you that were somewhat confused. What happened was I downloaded the 6.10 release, but the process was the same. I'm just not sure if what I downloaded was the iso, since it was a zip file. Sorry about the](*,) headbanging, and thanks for sticking with me.

---

### Post by LLRNR on 2006-11-05
I don't happen to know the 6.10 release, but it must basically be the same with the 6.06. So the thing is that you have to download the Live CD if you want to make your life easier, if it comes as an iso you burn it directly to a CD blank (without making it bootable from the CD burning software you use), if it comes as a zip you unzip it and burn it accordingly (also without enabling the bootable CD option), then you insert the freshly-burned Live CD in your CDROM drive, then reboot, choose from BIOS the CD as the main boot device and then it should all come up by itself... My guess is that your problem resides in that darn "Make bootable CD" option... It's just a guess but if I were in your place, I'd try to burn another CD without enabling this option and see what happens.

Good luck !

LLRNR

---

### Post by Bartender on 2006-11-05
> **FFfanatic said:**
> Is it possible that Ubuntu doesn't want to dual boot with Windows for some reason?

At this point all you're trying to do is get the PC to recognize the CD as a bootable device, so the problem has nothing to do with Windows or Ubuntu having a disagreement.  The PC has no idea if an operating system even exists until it moves on from BIOS and begins to hunt for one that it can start up.  When the PC is set up to "boot" from the optical drive, it should do so even if there's no hard drive, and no Windows OS, at all.
What happens if you make no changes to BIOS and remove the CD?  Same thing, or does Windows start up like normal?  If it goes to the A: prompt with no CD in the tray there's something wrong with the changes you made in BIOS.
I still don't understand the .zip thing.  You mention it again in the last post.  Where did you go for the download?  On the official ubuntu download sites it is not a zipped file.

---

### Post by FFfanatic on 2006-11-05
If there isn't a CD, then it boots directly into Windows.

With the file (.rar), I go to downloads on ubuntu.com, click on Canada for the 6.06 versions, then I download the -desktop-i386.iso.

I think that it only downloads as a Winrar file is if you don't have any CD burning software that supports iso burning because my computer doesn't have any software but my laptop does and on my laptop it wants to save it as an NTI....iso

---

### Post by LLRNR on 2006-11-05
Alright, I took a look on the Download section from ubuntu.com, I went to 6.06 LTS section, I clicked on the first Canada tab, I then chose i386-desktop.iso file... and boom! A popup appeared asking me wether I wanted to save the ~700 ISO file. Note: when you hold your mouse pointer over the link for the iso you want to download, you can see where the link points to in the lower bar ("status" bar ?!) of your browser - mine is Firefox and right now I'm on Dapper, so I don't have any special software installed, just the default ones, and - also - on Windows XP the thing is basically the same - I get an iso... Ok, first thing to do would be to grab a CD burning tool and install it on the computer you use to download your iso file on. If you still have problems, you might as well try to download the .torrent file... but it's a little bit more annoying, you'll then have to download a client like [utorrent](http://utorrent.com/download.php), install it, add the .torrent file to your download list... prey that there are enought seeds and so on.

Good luck!

LLRNR

---

### Post by FFfanatic on 2006-11-05
I chose to torrent it, should be finished in a couple hours.

I have to torrent it though because I've found that:
a) unless there are only a few seeds, website downloading is way slower.
b) website downloads from ubuntu.com often cut out and I'm forced to download it again, since it wipes the file if it doesn't complete, and hope it doesn't cut out before it finishes.

---

### Post by Bartender on 2006-11-06
On a Windows PC, I always download from Firefox, ask FF to "Save" to the desktop, then leave it alone while it's downloading.  Don't do anything to distract the PC from the task at hand. 
Then I make a folder under C: Drive, call it 'Xubuntu', 'Kubuntu' or whatever and right-click drag the file to the new folder.  Choose "Move".  Then I check the md5 again.
If you want to download it from your desktop, then burn it on your lappy, do you have a big enuf thumb drive to simply transfer it?
I have NTI version 7.  All I do is double-click on the downloaded .iso, and NTI does the rest.  It starts up, asks how I want to burn (8X is the slowest option - fortunately 3 GHz Pentium 4 and 2 GB of RAM have handled that so far) and proceeds.  I made the mistake once of opening NTI first and clicking on the file - it made a data copy instead of converting the .iso!

---

### Post by FFfanatic on 2006-11-08
OK, liveCD is up and running. But now I have a somewhat related question. I'm trying Ubuntu on my laptop and I need to know if there is a way to change the mouse settings BECAUSE whenever I open something(double click), then try to move away from it, it drags the icon, or whatever I opened. I guess this is due to my not having a mouse, but is there any way around that? Ie. decreasing sensitivity or something.

---

