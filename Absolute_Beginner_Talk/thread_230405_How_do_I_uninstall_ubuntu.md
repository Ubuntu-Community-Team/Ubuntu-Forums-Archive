---
title: "How do I uninstall ubuntu?"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Ubunoob06 on 2006-08-05
Alright I installed ubuntu about 2 weeks ago I love the os but It doesn't recognize my soundcard or modem. THe only problem I have is that I use this pc for recording. I was wondering how I can uninstall ubuntu completely so I can partition my hard drive and run win 98 (yeah yeah I know don't spit drink on your screen laughing) along with ubuntu Please help I've searched the forums but I can'tfind anything that will work. I've tried a boot disk and it tells me nonsystem disk replace and retry. I'tried to boot from the cd but it just goes straight to ubuntu, and it's a little more than frustrating. Please help!!!

Thanks

---

### Post by Herman on 2006-08-05
Please post again if you don't find all the answers you need on the following web page,                     How to Uninstall Ubuntu........................................................................[Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
Regards, Herman :D

---

### Post by orb9220 on 2006-08-05
You will need a win98 startup disk that has the fdisk command.

Boot with floopy startup disk. At the A>
fdisk /mbr

NOTE: The fdisk /mbr command only re-writes the MBR on the system drive (DISK-0) using BIOS calls. You cannot specify any other drive for the fdisk /mbr command to operate on other than DISK-0.

Hope this helped

---

### Post by Ubunoob06 on 2006-08-07
still can't get it. I got the boot disk from bootdisk.com but I can't get to the A:. I feel like a moron at this. Can someone give me some screen shots of where I need to go?

---

### Post by Sal33n on 2006-08-07
Yay!!!  My first post on these forums and it's to answer a DOS question!!!  lol

Ok, here we go:

***I've tried a boot disk and it tells me nonsystem disk replace and retry. ***

What this means is that your boot disk isn't really a boot disk.  It doesn't have the files you need for it to boot.  Now I am assuming that since you want to load Win98 that you have a Win98 CD correct?  If you do then chances are that it's a bootable CD.  What you need to do is boot your PC with your Win98 CD.  When it first starts boot from CD, start taping the F8 key a few times.  This should give you a menu to choose from.  Pick the option for command prompt only.  That way it will boot like a standard DOS boot disk and load the CDROM drivers.  Once it's done booting you will be left at a DOS prompt and depending on your configuration it could be A: C: or D: or whatever.  Do a DIR command to see where it leaves you and what files are in there.  You need to find the win98 directory.  The fdisk command should be in there.  I say should be because I just checked a win98 CD I have here and it's not there but it's not the 2nd edition 98 either. I found it in the base4.cab CAB file.  If this is your situation than you can use the extract command in the Win98 folder and extract fdisk to a floppy and run it from there.  

All this typing makes it sound more difficult than it really is.  Hopefully you know your DOS!     :)

Good Luck

---

### Post by Herman on 2006-08-08
> still can't get it. I got the boot disk from bootdisk.com but I can't get to the A:. I feel like a moron at this. Can someone give me some screen shots of where I need to go?
           Ubunoob06, Thanks for letting me know about that problem. 
Maybe the **98SE OEM **Self Extractor file download from [Bootdisk.com]("http://www.bootdisk.com/"). has been updated to a newer version than the one I used to make the instructions for that web-page. I have downloaded an up to date version and tested it and improved those instructions , (thanks to your feedback). Please check those instructions again now that I have fixed them, and remember to click the 'refresh' button on your browser to get the updated version of that webpage. And thank you for letting me know about the problem. Sorry for any inconvenience. 
All the best, regards, Herman :D

EDIT: To be fair to sal33n, most windows89 boot disks would probably be like sal33n is typing about. I have emphasised more now that it's the 98seOEM from Bootdisk.com that I'm referring to where I might not have stressed that enough before. Thanks for your input, sal33n, and welcome. :D

---

### Post by Ubunoob06 on 2006-08-08
Thanks Herman I hope I can figure this out. I'm going to do some research and learn more about Ubu before I go back to it.

---

