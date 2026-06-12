---
title: "Rescuing Files from a Bad HD"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Sef on 2006-09-26
Have a friend who has a bad hard disk at work.  It starts to boot then stops when it checks for cd rom for a disk.  I was wondering what's best to use to get the files he wants to save off the hard disk? (Ubuntu, Xubuntu, or other.)

His machine has the following: 

Windows 98 first Edition

6.4 gb hd
192 ram
500 MHz

(On the bright side, there are plans to update the computers to Windows XP.)

---

### Post by Mr Frosti on 2006-09-26
I would personally recommend using a Knoppix disc. The last I checked, the Ubuntu 6.06 CD in live mode had some issues mounting a hard drive on the machine that it was booted in. 

With Knoppix, you can boot to the CD, and then click on the "hda" icon on your desktop to browse the files. 

You can then transfer these files to a USB drive, or send them across the Internet to some other place. 

Good luck!

---

### Post by whizbaby on 2006-09-26
> **Sef said:**
> Have a friend who has a bad hard disk at work.  It starts to boot then stops when it checks for cd rom for a disk.  I was wondering what's best to use to get the files he wants to save off the hard disk? (Ubuntu, Xubuntu, or other.)

I've got quite good experiences with knoppix as a rescue system, it provides some useful tools (**testdisk** in your case)
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
> 
(On the bright side, there are plans to update the computers to Windows XP.)
Don't see too much improvement here...(don't you have to buy new hardware, too , or does 98 run on novadays hardware?)

---

### Post by RoamenCota on 2006-09-26
out of my personal experiences i would have to say a good route to take would be to just plop the 6.4gb into an external hd enclosure if you have one or know someone that does and copy the files over to another computer for storage sake.  the knoppix idea that ^dude^ had isnt a bad idea either.

---

### Post by Sef on 2006-09-26
Thanks for the suggestions.  Think Knoppix is the way I will go.

---

### Post by DarkKoopa on 2006-09-27
I've always used SpinRite from [http://www.grc.com](http://www.grc.com)

It's OS independant and has worked every single time I've had to use it. (Twice with work's Seagate HDDs, and my Samsung HDD).

The downside is that it's not free.

I like the idea of using a LiveCD, if you choose this method, can you post back if it worked or not?

---

### Post by cotcot on 2006-09-27
Following is worth a try because it saves you from reinstalling windows. 
Partimage the w98 partition to a DVD or an external hdd using a livedCD and restore after replacement of the failing hd.
Quite some liveCD have problems with partimage to an external hdd with USB 2.0 connection. I use the Gentoo liveCD for that. Kanotix (a debian version of knoppix) works as well, but is not simple in changing the permissions of the devices.

---

### Post by Sef on 2006-10-19
> I like the idea of using a LiveCD, if you choose this method, can you post back if it worked or not?

I used Knoppix and it worked just fine.  Download his files to some floppies and then found out he had a usb key.  So backed them up on there too, along with some pics and folders.

---

### Post by viper on 2006-10-19
You might want to try Hiren`s Boot CD from this link [http://homepage.ntlworld.com/hiren.thanki/bootcd.html](http://homepage.ntlworld.com/hiren.thanki/bootcd.html)

---

### Post by dolphinsonar on 2006-10-19
Try getting it from bit torrent it wont cost you anything.

---

### Post by mcduck on 2006-10-19
in worst cases cooling the harddisk may help too. So if you have troubles copying the files even with a live-cd, remove the drive, put it in a freezer for a while, plug it in, save some files to another disk, and repeat until you have rescued everything you need.

---

### Post by viper on 2006-10-19
Wow freezing the HD thats a new one, does it really work?

---

### Post by Sef on 2006-10-19
> in worst cases cooling the harddisk may help too. 

Makes sense.  By cooling the harddrive, it would contract.  By contracting, it would decrease the space inside the harddrive.

---

### Post by az on 2006-10-19
If you can, the first thing to do is image the drive.  If you can use an external drive enclosure or put it into another box with a second hard drive, use dd to dump the data into a file.  

Then use tools to access the data on it.  I have had a lot of success with foremost ([http://foremost.sourceforge.net/)](http://foremost.sourceforge.net/)).  It is in the repos, but the version is too old.  You can compile it from source and run it.

---

