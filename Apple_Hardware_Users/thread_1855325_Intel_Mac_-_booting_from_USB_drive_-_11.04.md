---
title: "Intel Mac - booting from USB drive - 11.04"
date: 2011-10-05
forum: Apple Hardware Users
---

### Post by Der_Kommissar on 2011-10-05
I'm trying to help someone at work make an Intel Mac bootable USB thumb drive (Patriot XT 8GB)  for Ubuntu so that they can use it for a class they're teaching next Spring.  (Lots of F/OSS discussion in the class, so he wants the students to be able to check out Ubuntu)

I saw the note on the [download page]("http://www.ubuntu.com/download/ubuntu/download") about the mac.  I followed the directions, and now I've got a USB drive that the Mac sees as a volume.  (Of course if I pop it into my Ubuntu machine it says "A Volume with software packages has been detected...." ;))

I've tried booting the mac using the Option / Alt key, but it doesn't show the USB drive.  The Mac I'm using is dual boot (OS X (10.5.8 -  and Windows XPSP3).  I thought maybe refit on the Mac was causing problems, so I checked another machine (only OS X 10.5.8 -  and had the same result.  The Mac will recognize the internal HDD, but not the USB drive with the image.

I checked to make sure the USB thumb drive is formatted with the GUID partition scheme.  When I ran the "sudo dd if=/...." command though it appears that it set the drive back to a Partition Map Scheme of "unformatted."

I'm stuck at this point.  Please help. :smile:

Below are the instructions I followed.
--------------
             **Mac**

         
                      We would encourage Mac users to download Ubuntu Desktop Edition by  burning a CD for the time being. But if you would prefer to use a USB,  please follow the instructions below.
              
             Note: this procedure requires an .img file that you will be required to create from the .iso file you download.
              
             TIP: *Drag and Drop* a file from Finder to Terminal to 'paste' the full path without typing and risking type errors.
              
             
[LIST=1]
[*]Download the desired file
[*]Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
[*]Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
[*]                     **Note:** OS X tends to put the .dmg ending on the output file automatically.
[*]Run diskutil list to get the current list of devices
[*]Insert your flash media
[*]Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
[*]Run diskutil unmountDisk /dev/diskN (replace *N* with the disk number from the last command; in the previous example, *N* would be 2)
[*]Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
[*]
[LIST]
[*]Using /dev/rdisk instead of /dev/disk may be faster.
[*]If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
[*]If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
[/LIST]
 
[*]Run diskutil eject /dev/diskN and remove your flash media when the command completes
[*]Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick
[/LIST]

---

### Post by meatytaco on 2011-10-06
If you are going for a live version of Ubuntu, I would suggest using the Linux live USB creator to do it.  Very user friendly and you can set persistence. That way you'll be able to save files and whatnot to the USB. It's you own little portable operating system :P You'll need the .iso file of the Ubuntu version you are wanting to run, and the Linux live USB creator software.

Linux Live USB Creator: [http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

---

### Post by pindar on 2011-10-06
> **Der_Kommissar said:**
> I'm stuck at this point.  Please help. :smile:


Use the search, Luke: [http://ubuntuforums.org/showthread.php?t=1851167]("http://ubuntuforums.org/showthread.php?t=1851167")

---

### Post by Der_Kommissar on 2011-10-06
> **pindar said:**
> Use the search, Luke: [http://ubuntuforums.org/showthread.php?t=1851167](http://ubuntuforums.org/showthread.php?t=1851167)

I apologize if I didn't phrase that correctly.  I did search, but my Google-Fu was weak yesterday.

Going to have another crack at it today - thank you for the suggestions.  Will let 'ya know how they turn out.

---

### Post by pindar on 2011-10-07
> **Der_Kommissar said:**
> Going to have another crack at it today - thank you for the suggestions.  Will let 'ya know how they turn out.
Please do let us know how things went (as you see in the other thread, most posters disappear into the sunset and are never heard of again). And don't be too disappointed if it doesn't work. Small anecdote: I prepared a 4 GB live USB of Oneiric with the method I linked to. It boots both my brand new MacBook Air and my rather old Mini. yesterday, I tried it on my new iMac - no go, if it's in a USB slot, it wouldn't even bring up the Apple boot loader, let alone refit. So: Apple hardware is very fickle in this regard, it may or may not work. Or, as they say about Microsoft products in Germany: mal Gates, mal Gates nicht...

---

### Post by penguinv on 2011-10-28
- Ubuntu-booting Ubuntu from USB drive - working on it -
Oct 28, 2011 -- Not Solved Yet --
Hi I'm working with me, Google-Fu and the Genius Bar on this - 2 GB appts plus talking to other "blueshirts" and following the advice. 

I have: Intel Macbook core 2 duo and 
        the file ubuntu-11.04-desktop-i386.iso

[INDENT]This paragraph and more will be repeated at the end of this post.
WHY am I doing this?  I want to read/write my Ubuntu 1T HD that I used on the PC-that-failed. The MacBook has a 0.072T (72GB) HD 
which was full.  Has 4.5GB free now. 
WHY NOT USE a liveCD? ...[/INDENT]

I've been doing this and that, talking twice to the genius bar about it. (And once to irc.freenode.net #MacOSX who banned me for suggesting I would talk to the genius bar after _they_ told me I could not do it and if I did it would damage my mac. I say: Question all authorities. But one kind one talked ot me in PM. But that was days ago.)

I've been logging what I did in detail and making a summary each time so I can keep track. I've made the disk with diskutility and again formatted first (Erase tab) with Mac Journaled format. There's a tricky bit I didnt expect where it cares if image or source disk iss either mounted or unmounted before it will drag into Disk Utility (found in the Finder Go Menu > Utility > Disk Utility).

One uses the option/alt key-holddown at boot to show all bootable drives and it did not show either time. 

I read I needed to convert it an .img file on this website
     [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

[INDENT]-- directions are to use terminal:
hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso
-- so I did
$ hdiutil convert -format UDRW -o ~/Users/username/Desktop/ubuntu-11.04-desktop-i386.img ~/Users/username/Desktop/ubuntu-11.04-desktop-i386.iso 
hdiutil: convert failed - No such file or directory
[/INDENT]

I repeated that in case I made a dumb-error-I-missed.

I went and googled more far and wide. So far nobody reports success. Speculation runs rampant as if the windows version will work on any intel. Meanwhile I've read something that suggests I can boot from a liveCD and make the USB from that. I havent checked on that. 
(All belief has been suspended, heh.)

-------------
I hope I've done the right thing by adding to this thread insteas of starting a new one. I thought it would be more helpful to all here.

Reminder of why:
WHY am I doing this?  I want to read/write my Ubuntu 1T HD that I used on the PC-that-failed. The MacBook has a 0.072T (72GB) HD 
which is full. 
WHY NOT USE a liveCD? Because I need to have the non-free installed or I can't play videos. I need VLC. I'd like skype to be available, if possible. I'd like IRC and I know that Ubuntu dropped that in 10.04 so I had to install it. (I chose to use 11.04 for this and it and Unity will be new to me.)

NEXT STEP: I will burn a liveCD and see.

---

### Post by penguinv on 2011-10-29
continued from previous post:

So I can boot up from the liveCD "IF" I choose F-4 (Modes) on the "Try Ubuntu?" screen and then pick "Safe Graphics Mode". 

I did this with 9.04 and assume it will work with 11.04 (not tried yet). 

Still I cant read my hard drive because I dont have permissions. 
I've been told I can use sudo to do it. I've been given these two "hardly there" instructions on irc.freenode.net #ubuntu

helpful chatter 1: use gksudo nautilus
helpful chatter 2: gksu/dksudo

So far that's it.

---

