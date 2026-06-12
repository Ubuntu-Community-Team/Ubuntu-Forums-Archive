---
title: "won't open cd"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by hiffenscgaupher on 2006-11-04
The problem that I am having is I think I copied the cd correctly, but don't know. The computer recognizes the disk, I hope that's good. At reboot it goes to the windows login screen, and I have hit F5 button. Am I needing something to start the process for the disk, such as hardware or software. I'm confused about this.

---

### Post by taurus on 2006-11-04
First of, you need to make sure you burn the iso image that you have downloaded as an image file, not data file.  Then, you need to go into your BIOS and set the pc to boot from CD-ROM first, not the harddrive...

Have you done both of those?

---

### Post by hiffenscgaupher on 2006-11-04
There is an image. But heres a good one, I have no idea what I'm doing in the bios area, and I don't know what I'm supposed to change, it's all alien to me.

---

### Post by taurus on 2006-11-04
Do you have the manual for your computer or at least your motherboard?  It will tell you which key to press (Del, F2, etc.) when you first turn it on to get into your BIOS.  Use the arrows to navigate around until you get into a section about boot sequence.  In there, you want to change the order of boot from harddrive first to CD-ROM first...

What is the model of your computer anyway?

---

### Post by hiffenscgaupher on 2006-11-04
I have a compact presario, running xp, when I went into the bios I changed the order to the cd/rom first, that I did do. It booted in windows even after I pressed F5.

---

### Post by taurus on 2006-11-04
After you've changed the order of boot, you don't have to hold anything.  Just insert Ubuntu CD, assuming that you have burned it as image file, not data file, and reboot.  And before you reboot, look into the CD and see if there is one large file and a few files and a bunch of directories/folders.  If you see one large file, then you burned it wrong.  In other words, you should see a bunch of directories/folders on it...

---

### Post by hiffenscgaupher on 2006-11-04
I did a search on the disk from the My Computer screen and nothing was listed. So how do I get into the disk to see.

---

### Post by Bartender on 2006-11-04
Also, you may want to go back into your BIOS and make sure that you did change the boot setting so that the PC looks to the optical drive first.  It's easy to think you made a change and get out of BIOS without actually saving the change.  
Then, as taurus, said, you don't touch anything after restarting the PC.  Watch your optical drive.  The light should come on and the drive should spin up.  If it boots into Windows anyways then there are 2 likely options.  Either the PC is STILL not set up to boot from the CD, or it looked at the CD, decided that the CD was not a bootable device, and moved on to the HDD.
Taurus' suggestion to look at the CD is also very appropriate.  If you're in Windows, toss the CD in the tray, and Explore it.  Don't try to start it, run it, etc.  You should see several folders and a couple of files.

---

### Post by Bartender on 2006-11-04
Try Windows Explorer.  Go to your D: drive (I assume).  Your PC sees nothing?  Do you mean it sees no CD at all or is unable to read its contents when you click on it?

---

### Post by hiffenscgaupher on 2006-11-04
I did the explore as you said bartender and it only showed one item describing ubuntu. nothing else.

---

### Post by hiffenscgaupher on 2006-11-04
I beleive that it does not see anything but that one item, no other files or folders. I am starting to think that it did not copy the program.

---

### Post by Bartender on 2006-11-04
OK, sounds like what you did was copied the .iso download, not converted it to a bootable CD.  This is a fairly simple concept, but constantly trips people up who haven't dealt with this before.   The download is not the CD.  The download must be concverted to a bootable CD by either your installed burning software, or one of several utilities that have been suggested numerous times here on the forums.
What's your burning utility?  Nero? Adaptec? NTI?
Another question: do you have the download still saved to a folder?  In other words, we can try again, right?

---

### Post by hiffenscgaupher on 2006-11-04
windows cd wizard. I get the idea that's not going to work. I need something else, don't I?

---

### Post by Bartender on 2006-11-04
[Here's]("http://www.ubuntuforums.org/showthread.php?t=278736&highlight=burning+iso") a recent discussion with some links
Another [one]("http://www.ubuntuforums.org/showthread.php?t=278736&highlight=burning+iso")

---

### Post by taurus on 2006-11-04
Here's a link for you to read...

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by hiffenscgaupher on 2006-11-04
Well I brought the program down again, and the same thing happened again, one file, that's it!!!! I followed the instructions to the best of my beginners intelligence, and wasted 5 cd's in the process. Do I or don't I need another program to bring this os into the works. From the screen shots it looks like I need another program to make this happen. If not I need step by step instructions to do this process.

---

### Post by taurus on 2006-11-04
What Windows software do you use to burn your CDs?  There are a few you can download for free and CDBurner is one that shows you in the link that I have sent...  You can get a copy for your XP right here.

[http://www.cdburnerxp.se/](http://www.cdburnerxp.se/)

---

### Post by rsambuca on 2006-11-04
It really sounds to me like you are not burning an image cd.  There is a difference between burning a data CD and an iso image CD.

---

